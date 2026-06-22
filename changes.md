# Project Changes

- Added a custom torque control scheduler task to `ArduCopter/Copter.cpp`:
  - `SCHED_TASK_CLASS(Copter, &copter, torque_control_update, 400, 50, 20)`
- Added `Copter::torque_control_update()` wrapper to call `torque_ctrl.update()`.
- Added `torque_ctrl.init();` to `Copter::init_ardupilot()` in `ArduCopter/system.cpp` so the library is initialized during startup.
- Corrected formatting of the `torque_control_update` method definition in `ArduCopter/Copter.cpp`.
- The project now includes the custom `AP_TorqueControl` library and registers it for build via `wscript`.
- Confirmed `AP_TorqueControl` is declared in `ArduCopter/Copter.h` and used as `AP_TorqueControl torque_ctrl;`.

## Notes

- Scheduler task parameters are: `400` Hz, `50` microseconds budget, `20` priority.
- Initialization occurs before the normal scheduler loop begins, during Copter startup.
