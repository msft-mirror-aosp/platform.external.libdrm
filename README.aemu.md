# Generating Bazel Build Files for libdrm (AEMU)

This document explains how to generate Bazel build files for the `libdrm` project, specifically for use within the Android Emulator (AEMU) development environment.

## Purpose

The `aemu-bazel/generate_bazel_files.sh` script automates the creation of Bazel `BUILD` files for `libdrm` using the `amc.py` toolchain script. This allows `libdrm` to be built and integrated into a Bazel-based AEMU project.

## Prerequisites

*   An Android Open Source Project (AOSP) checkout.
*   The `amc.py` toolchain script available at `$AOSP_ROOT/hardware/google/aemu/tools/toolchain/src/amc.py`.

## How to Generate Bazel Files

1.  **Navigate to the `libdrm` repository root:**
    The `generate_bazel_files.sh` script is designed to be run from the top-level `libdrm` directory.

    ```bash
    cd /path/to/your/aosp/third_party/libdrm
    ```

2.  **Run the generation script:**
    Execute the script from the `libdrm` root. The script will automatically deduce the `AOSP_ROOT` based on its own location (assuming it's in `$AOSP_ROOT/third_party/libdrm/aemu-bazel`).

    ```bash
    ./aemu-bazel/generate_bazel_files.sh
    ```

## What the Script Does

*   **Deduces `AOSP_ROOT`**: It determines the root of your AOSP checkout.
*   **Changes Directory**: It changes the current working directory to the `libdrm` repository root (`third_party/libdrm`).
*   **Executes `amc.py`**: It calls the `amc.py` script with the necessary configuration files (`aemu-bazel/aemu-drm-build-config.jsonc` and `aemu-bazel/aemu-drm-shim.jsonc`) to generate the Bazel build files.

## Output

The generated Bazel build files will be placed in the `amc-build` directory within the `libdrm` repository root (e.g., `/path/to/your/aosp/third_party/libdrm/amc-build`).
