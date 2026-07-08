# rock64-os-build

This repository is intentionally dedicated to **OS image build automation only**.

## Separation of concerns

- **`rock64-os-build` (this repo):** Armbian image build configuration only (`.github/workflows/` and optional `userpatches/`).
- **`rock64-robot-src`:** ROS 2 workspace, Python nodes, C++ drivers, and robot application code.

Keeping these repositories separate keeps CI predictable and makes OS-image changes easier to audit.

## "Gold mine" strategy

If you have an older mixed-purpose repository, keep it as a reference library. Copy over only proven, current logic (for example, startup scripts and udev rules), and leave outdated/conflicting setup behind.

## CI/CD workflow for this repository

1. Trigger **Build ROCK64 Armbian Image** from Actions.
2. Download the produced image artifact.
3. Flash to SD card.
4. Clone `rock64-robot-src` onto the device and build robot software there.
