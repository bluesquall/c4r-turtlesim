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

_____________
[tutorial-turtlesim]: https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html
_____________

