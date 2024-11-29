# ani-MR24
supporting material for Rappisi et al 2025: "3-D Mantle Flow and Structure of the Mediterranean from Combined P-wave and Splitting Intensity Anisotropic Tomography"

This repository contains the files required to plot and analyze the tomographic model and the related reference model described in “3-D Mantle Flow and Structure of the Mediterranean from Combined P-wave and Splitting Intensity Anisotropic Tomography”

Please contact francescorappisi@gmail.com for further assistance

File Contents:

1. srGeometry.mat
Contains information on geographical coordinates (latitude and longitude) required to plot the tomographic model.

2. srModel_RefMod_AK135.mat
Includes the AK135 reference model interpolated on the 3D computational grid.

3. srModel_aniMR24.mat
Contains the tomographic model, including:
- P wave velocity.
- P wave anisotropy.

4. VTK files (see below)


Calculations in MATLAB

After loading the files into MATLAB, isotropic velocities and velocity anomalies can be computed as follows:

Isotropic Velocity and Velocity Anomalies

1. Load the reference model:

   	U = refModel.P.u; % Reference model slowness

2. Compute the mean velocity:

	Vmean = 1 ./ aniMR24.P.u; % Mean velocity from aniMR24

3. Compute the isotropic velocity (i.e., accounting for anisotropy effects):

	Viso = Vmean .* (3 - 0.5 .* aniMR24.anis_fraction_P) ./ 3; 

4. Compute velocity anomalies from Viso:

	dlnV = (Viso - (1 ./ U)) ./ (1 ./ U); % Relative anomalies

5. Alternatively compute velocity anomalies from Vmean (not recommended):

	dlnV = U .* ((1 ./ aniMR24.P.u) - (1 ./ U)); % does not account for anisotropy


Note: It is recommended to use Viso because it accounts for anisotropy, providing a more accurate velocity value in this context.


Files for 3D Model Plots
The following files in VTK format are provided for visualizing the 3D slab models (isotropic velocity anomalies (dlnViso) and anisotropy patterns):
	•	aniMR24.vtk: Full model.
	•	Alboran.vtk: Slab model in the Alboran region.
	•	Alps.vtk: Slab model in the Alps region.
	•	Apennines.vtk: Slab model in the Apennines region.
	•	Carpathians.vtk: Slab model in the Carpathians region.
	•	Cyprus.vtk: Slab model in the Cyprus region.
	•	Hellenic.vtk: Slab model in the Hellenic region.
