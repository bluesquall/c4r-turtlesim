# turtles

## containerized development

### starting in foreground (or `tmux`)

```
podman container run --rm -it \
  --network host --ipc host \
  --volume=/tmp/.X11-unix:/tmp/X11-unix:rw \
  --volume=/dev/dri:/dev/dri:rw \
  --env=DISPLAY \
  ghcr.io/bluesquall/c4r-turtlesim:jazzy-desktop-full
```

### starting with quadlet via `systemd`
> [!NOTE]
> This seems a worthwhile avenue to explore, especially for containerized
> services that need to start on boot on a robot runnning a distribution
> that uses `systemd`. It may be less directly applicable to the graphical
> application used in this example.

## tutorial-turtlesim

Following along with [the official tutorial][tutorial-turtlesim]:
```
ros2 pkg executables turtlesim
```
returns:
```
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node
```
as expected.

But trying to actually run `turtlesim`:
```
ros2 run turtlesim turtlesim_node
```
results in a MESA error:
```
...
MESA: error: Failed to query drm device.
glx: failed to create dri3 screen
failed to load driver: iris
failed to open /dev/dri/card1: No such file or directory
failed to load driver: iris
```
Adding a bind-mount to `--volume=/dev/dri:/dev/dri:rw` fixes the problem, and now:
```
ros2 run turtlesim turtlesim_node
```
produces the simulator window with a random turtle in the center.

Starting:
```
rqt
```
opens the graphical window, as expected.
I can spawn a new turtle, change the color of its trail with `SetPen`,
and teleoperate each of them by using separate `tmux` panes running:
```
ros2 turtlesim turtle_node
```
and
```
ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=raph/cmd_vel
```
_____________
[tutorial-turtlesim]: https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html
_____________

