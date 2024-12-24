# vex-dashboard
Dashboard for telemetry from VEX V5 Brain

## Example usage
```cpp
template <typename T> void log_helper(const T& value) { std::cout << value; }

template <typename T, typename U, typename... Args> void log_helper(const T& key, const U& value, const Args&... args) {
    std::cout << key << "=" << value;
    if constexpr (sizeof...(args) > 0) {
        std::cout << ",";
        log_helper(args...);
    }
}

template <typename... Args> void log(const Args&... args) {
    std::cout << "VEX_DASHBOARD_BEGIN" << pros::millis() << ",";
    log_helper(args...);
    std::cout << "VEX_DASHBOARD_END" << std::flush;
}

log("Left desired", leftVelRpm, "Right desired", rightVelRpm, "Left actual", left.get_actual_velocity(),
    "Right actual", right.get_actual_velocity());
```
