# T513---SIEngineDynamometer
This model contains a multi-input multi-output (MIMO) control for the air flow components (specifically the throttle and wastegate valves) in the MathWorks’ SI Engine Dynamometer in the Powertrain Blockset, a simulated gasoline engine. This MIMO approach uses a set of separate scheduled linear model predictive controllers (MPC) for both the throttle and wastegate to improve the engine’s transient torque tracking. The controllers use an intake manifold pressure (MAP) reference and measured output; a torque-MAP lookup table will be used to convert the commanded torque to a MAP command to be input into the controller (for now a manual MAP command is being used).

The pdf document entitled Final System Review April 2021.pdf contains our modeling approach, our progress, and our results.

OperationManual.pdf details the changes to the base SIDynoReferenceApplication that need to be made to run this modification.

CreateDiffMPC contains the MATLAB files to automate the collection of data and the creation of MPC objects used for the controller. Run with the Simulink model from SIDynamometer_Data_Collection.

SIDynamometer_Data_Collection contains the Simulink model (SIDynoReferenceApplication.slx) to replace a new/unaltered SIDynoReferenceApplication, and collects data to create MPC objects. Change the path referenced in line 35 of the RunMe in the CreateDiffMPC folder to the .prj file in this new SIDynamometer folder as follows: .../SiDynamometer/main/SIDynamometer.prj.

SIDynamometer_MPC_Testing contains the Simulink model to test created MPC objects (SIDynoReferenceApplication.slx), as well as the model for the controller (SiEngineController.slx). To run this, replace the SIDynoReferenceApplication as before, and also replace the SiEngineController in SIDynamometer/refs/SIEngine/Controller/SiEngineController.slx.
