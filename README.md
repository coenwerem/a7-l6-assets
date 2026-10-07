# A7/L6 Assets

A7 robot with bilateral Linker L6 hands, assembled for IsaacLab simulation.
Model assembly and IsaacLab conversion by the repository author.

`robot.usdc` is a self-contained USD articulation with embedded meshes, collision
geometry, inertias, joint limits and mimic relationships. It uses Isaac Sim's
built-in OmniPBR material. `manifest.json` records its SHA256 digest.

## Clone

```bash
git clone https://github.com/EXACT-lab/a7-l6-assets.git
```

## Loading

Use the absolute path to `robot.usdc` with IsaacLab's `UsdFileCfg` in an
`ArticulationCfg`. Tested with IsaacLab v2.3.2 and Isaac Sim 5.1.0.
Supply scene placement, initial joint positions and actuator settings in the
application that loads the model.

## L6 joint coupling

Both hands include five PhysX mimic constraints. The passive thumb joint follows
`thumb_cmc_pitch` with an angle multiplier of **2.22**; each passive finger DIP
joint follows its MCP pitch joint with a multiplier of **1.9**. All offsets are
zero. The left thumb follower is named `lh_thumb_dip`; the right is
`rh_thumb_ip`.

These multipliers match RealHand's
[right L6 URDF](https://github.com/RealHand-Robotics/Realhand_description/blob/7a64d077ea8f1b81cd4df1f7b472ae3dece1b0ed/l6/right/realhand_l6_right.urdf)
and
[left L6 URDF](https://github.com/RealHand-Robotics/Realhand_description/blob/7a64d077ea8f1b81cd4df1f7b472ae3dece1b0ed/l6/left/realhand_l6_left.urdf).
They describe passive-joint kinematics, not motor reduction ratios.

PhysX defines `follower + gearing * source + offset = 0`, so the authored
gearing values are **-2.22** for thumbs and **-1.9** for fingers. Passive-joint
drives have zero stiffness, damping and maximum force. Configure hand actuators
for the six independent joints per hand; the mimic constraints transmit effort
to the five passive joints. Existing joint limits also bound the coupled motion.

## Model and attribution

The asset derives from the A7/L6 workcell model in MuJoCoDex and includes
XR Robotics assets. The repository author’s contribution is released under the
[MIT License](LICENSE). Upstream XR Robotics
material retains its [original MIT notice](LICENSE.XRoboToolkit).
