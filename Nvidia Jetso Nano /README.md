# Running and Building the Jetson-Inference Project

This guide provides instructions on how to run and build the **jetson-inference** project, whether using a Docker container or building directly from source. Follow the steps according to your preferred setup.

---

## Table of Contents
- [Running the Docker Container](#running-the-docker-container)
- [Building the Project from Source](#building-the-project-from-source)
- [System Requirements](#system-requirements)
- [Optional: ROS Support](#ros-support)
- [Running Example Applications](#running-applications)
- [Optional: Building the Docker Container](#building-the-container)
- [Optional: Installing PyTorch](#installing-pytorch)

---

## Running the Docker Container

The pre-built Docker container for **jetson-inference** is available on [DockerHub](https://hub.docker.com/r/dustynv/jetson-inference/tags). To run the project using Docker, follow these steps:

1. **Clone the Repository:**

   ```bash
   git clone --recursive --depth=1 https://github.com/dusty-nv/jetson-inference
   cd jetson-inference
   ```

2. **Launch the Docker Container:**

   Run the provided script to launch the container:
   
   ```bash
   docker/run.sh
   ```

   This script will automatically pull the appropriate Docker image based on your JetPack version and mount the necessary directories for data and devices.

3. **For x86 Support:**

   If you are running the project on x86 systems (instead of Jetson hardware), ensure you have [NVIDIA drivers](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#pre-requisites) and [NVIDIA Container Runtime](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/nvidia-docker.html) installed. You can then run the same `docker/run.sh` script as above.

### Mounted Data Volumes

The following directories are automatically mounted from your host device into the Docker container:
- `jetson-inference/data`
- `jetson-inference/python/training/classification/data`
- `jetson-inference/python/training/classification/models`
- `jetson-inference/python/training/detection/ssd/data`
- `jetson-inference/python/training/detection/ssd/models`

### ROS Support

For ROS/ROS2 support, you can specify the ROS distro while launching the container:

```bash
docker/run.sh --ros=humble
```

Supported ROS distros: Noetic, Foxy, Galactic, Humble, Iron.

---

## Building the Project from Source

To build the project directly on your Jetson device, follow these steps:

1. **Install Required Dependencies:**

   ```bash
   sudo apt-get update
   sudo apt-get install git cmake libpython3-dev python3-numpy
   ```

2. **Clone the Repository:**

   ```bash
   git clone --recursive https://github.com/dusty-nv/jetson-inference
   cd jetson-inference
   ```

3. **Build the Project:**

   Create a build directory, configure the project, and compile the code:
   
   ```bash
   mkdir build
   cd build
   cmake ../
   make -j$(nproc)
   sudo make install
   sudo ldconfig
   ```

   The compiled binaries will be available in the `build/aarch64/bin/` directory.

4. **Optional: Installing PyTorch**

   During the build process, you will be prompted to install PyTorch for transfer learning:

   ```bash
   cd jetson-inference/build
   ./install-pytorch.sh
   ```

   If you skip this step, you can run the command later to install PyTorch.

---

## Running Applications

After building or launching the Docker container, you can run example applications:

```bash
cd build/aarch64/bin
./video-viewer /dev/video0
./imagenet images/jellyfish.jpg images/test/jellyfish.jpg
./detectnet images/peds_0.jpg images/test/peds_0.jpg
```

To exit the container, press `Ctrl+D`.

For more information about the available applications, refer to the [API Reference](../README.md#api-reference).

---

## Building the Docker Container

If you prefer to build the Docker container from source, use the following command:

```bash
docker/build.sh
```

This command builds the Docker container using the provided `Dockerfile`.

---

## System Requirements

- **Jetson device** with JetPack 4.4 or higher.
- **NVIDIA GPU** with Docker and CUDA support for x86_64 systems.
- Optional: ROS/ROS2 support for ROS-based projects.

---

For further information, refer to the **[Hello AI World](../README.md#hello-ai-world)** tutorial.
