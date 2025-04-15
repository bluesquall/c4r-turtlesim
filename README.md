# turtles

## containerized development

### starting in foreground (or `tmux`)

```
podman container run --rm -it \
  --network host --ipc host \
  --volume=/tmp/.X11-unix:/tmp/X11-unix:rw --env=DISPLAY \
  ghcr.io/bluesquall/c4r-turtlesim:jazzy-desktop-full
```

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

_____________
[tutorial-turtlesim]: https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html
_____________

