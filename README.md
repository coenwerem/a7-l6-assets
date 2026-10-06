# A7/L6 Assets

A7 robot with bilateral Linker L6 hands, assembled for IsaacLab simulation.
Model assembly and IsaacLab conversion by the repository author.

`robot.usdc` is a self-contained USD articulation with embedded meshes, collision
geometry, inertias, joint limits and mimic relationships. It uses Isaac Sim's
built-in OmniPBR material. `manifest.json` records its SHA256 digest.

## Clone

```bash
git clone https://github.com/coenwerem/a7-l6-assets.git
```

## Loading

Use the absolute path to `robot.usdc` with IsaacLab's `UsdFileCfg` in an
`ArticulationCfg`. Tested with IsaacLab v2.3.2 and Isaac Sim 5.1.0.
Supply scene placement, initial joint positions and actuator settings in the
application that loads the model.

## Model and attribution

The asset derives from the A7/L6 workcell model in MuJoCoDex and includes
XR Robotics assets. The repository author’s contribution is released under the
[MIT License](LICENSE), also recorded in `LICENSE.MuJoCoDex`. Upstream XR Robotics
material retains its [original MIT notice](LICENSE.XRoboToolkit).
