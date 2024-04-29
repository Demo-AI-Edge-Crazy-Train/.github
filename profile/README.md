# The Crazy Train demo (with Artifical Intelligence and Edge Computing)

![](/profile/avatar.png)

## Abstract

Message to Ethan Hunt: *“The train is running mad at full speed and has no driver ! Your mission, should you choose to accept it, is to train and deploy an AI model at the edge that recognizes traffic signs in order to stop the train before it crashes. This message will self-destruct in five seconds. Four. three. Two. one.  tam tam tada tum tum tada tum tum tada tum tum tada tiduduuuuummmm tiduduuuuuuuuummm”*.

Full abstract [here](https://docs.google.com/document/d/135Y6yAEaJZleIXPm74G5dfwyMH8KfNT6hi4YLT4tCkw/edit).

## Software components

| Component | Description | Git Repository | Container Image |
| --- | --- | --- | --- |
| **train-controller** | Receives commands through MQTT and acts on the Lego Hub accordingly. | [Demo-AI-Edge-Crazy-Train/train-controller](https://github.com/Demo-AI-Edge-Crazy-Train/train-controller) | [quay.io/demo-ai-edge-crazy-train/train-controller](https://quay.io/repository/demo-ai-edge-crazy-train/train-controller) |
| **intelligent-train** | Receives images through MQTT, process them with an AI model and sends the results back to MQTT | [Demo-AI-Edge-Crazy-Train/intelligent-train](https://github.com/Demo-AI-Edge-Crazy-Train/intelligent-train) | [quay.io/demo-ai-edge-crazy-train/intelligent-train](https://quay.io/repository/demo-ai-edge-crazy-train/intelligent-train) |
| **train-ceq-app** | Manages messages between the train-controller, intelligent-train, capture-app, MQTT and Kafka. | [Demo-AI-Edge-Crazy-Train/train-ceq-app](https://github.com/Demo-AI-Edge-Crazy-Train/train-ceq-app) | [quay.io/demo-ai-edge-crazy-train/train-ceq-app](https://quay.io/repository/demo-ai-edge-crazy-train/train-ceq-app) |
| **train-monitoring-app** | Displays images streamed through Kafka. | [Demo-AI-Edge-Crazy-Train/train-monitoring-app](https://github.com/Demo-AI-Edge-Crazy-Train/train-monitoring-app) | [quay.io/demo-ai-edge-crazy-train/train-monitoring-app](https://quay.io/repository/demo-ai-edge-crazy-train/train-monitoring-app) |
| **train-capture-image-app** | Captures and compresses images from the webcam. Sends them over MQTT. | [Demo-AI-Edge-Crazy-Train/train-capture-image-app](https://github.com/Demo-AI-Edge-Crazy-Train/train-capture-image-app) | [quay.io/demo-ai-edge-crazy-train/train-capture-image-app](https://quay.io/repository/demo-ai-edge-crazy-train/train-capture-image-app) |

## Administration

- [rhde-nvidia-jetson-orin](https://github.com/Demo-AI-Edge-Crazy-Train/rhde-nvidia-jetson-orin): RHEL for Edge images for the Jetson Orin Nano
- [gitops](https://github.com/Demo-AI-Edge-Crazy-Train/gitops): OpenShift GitOps manifests

## Base container images

- [openjdk-opencv](https://quay.io/repository/demo-ai-edge-crazy-train/openjdk-opencv): OpenJDK + OpenCV base image for ARM64 and x86_64
- [nvcr.io/nvidia/l4t-jetpack](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/l4t-jetpack): NVidia Base image to leverage GPU acceleration on the Jetson Orin Nano

## Dependencies

### Bluetooth

- [node-ble](https://github.com/Demo-AI-Edge-Crazy-Train/node-ble): NodeJS library to use the BlueZ DBUS API under Linux
- [noble](https://github.com/Demo-AI-Edge-Crazy-Train/noble): NodeJS library that provides a cross-platform abstraction to communicate over Bluetooth Low Energy (BLE)
- [node-poweredup](https://github.com/Demo-AI-Edge-Crazy-Train/node-poweredup): NodeJS library that communicates with Lego hubs over Bluetooth Low Energy (BLE)

### OpenCV

- [cekit-images](https://github.com/Demo-AI-Edge-Crazy-Train/cekit-images): Cekit manifests to build OpenJDK images with OpenCV included
