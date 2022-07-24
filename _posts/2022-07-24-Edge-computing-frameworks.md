---
layout: post
read_time: true
show_date: true
title: "Edge computing frameworks"
date: 2022-07-24
img: posts/20220724/logo.png
tags: [Edge computing]
category: Edge computing
author: Peisong Li
description: "# Edge computing frameworks"
---
This is a collection of Edge computing frameworks. I shall test each framework and make a comparison in the future work.

## 1. Google Cloud IoT solutions
[Link:](https://cloud.google.com/solutions/iot)

Blog: [Bringing intelligence to the edge with Cloud IoT](https://cloud.google.com/blog/products/gcp/bringing-intelligence-edge-cloud-iot)
### Bringing machine learning to the edge

Today, we’re announcing two new products aimed at helping customers develop and deploy intelligent connected devices at scale: [Edge TPU](https://cloud.google.com/edge-tpu), a new hardware chip, and [Cloud IoT Edge](https://cloud.google.com/iot-edge), a software stack that extends Google Cloud’s powerful AI capability to gateways and connected devices. **This lets you build and train ML models in the cloud, then run those models on the Cloud IoT Edge device through the power of the Edge TPU hardware accelerator.**

![Google Edge](./assets/img/posts/20220724/Edge_TPU.png)

## 2. AWS IoT Greengrass (Amazon)
[Link:](https://aws.amazon.com/greengrass/)

AWS IoT Greengrass makes it easy to bring intelligence to edge devices, such as for anomaly detection in precision agriculture or powering autonomous devices.

![AWS Edge](./assets/img/posts/20220724/product-page-diagram_AWS-IoT-Greengrass.png)

## 3. NVIDIA EGX
[Link:](https://www.nvidia.com/en-us/data-center/products/egx/)

#### Powerful, Secure Acceleration from Data Center to Edge

The NVIDIA EGX platform delivers the power of accelerated computing from data center to edge with a range of optimized hardware, an easy-to-deploy, application and management software, and a vast ecosystem of partners who offer EGX through their products and services.

## 4. Huawei Kubeedge
[Link:](https://kubeedge.io/en/)

**KubeEdge** is an open source system extending native containerized application orchestration and device management to hosts at the Edge. It is built upon Kubernetes and provides core infrastructure support for networking, application deployment and metadata synchronization between cloud and edge. It also supports MQTT and allows developers to author custom logic and enable resource constrained device communication at the Edge. KubeEdge consists of a cloud part and an edge part. Both edge and cloud parts are now open-sourced.

![Kubeedge architecture](./assets/img/posts/20220724/kubeedge_arch.png)

## 5. Azure IoT Edge (Microsoft)
[Link:](https://azure.microsoft.com/en-us/services/iot-edge/)

#### Cloud intelligence deployed locally on IoT edge devices

Deploy Azure IoT Edge on premises to break up data silos and consolidate operational data at scale in the Azure Cloud. Remotely and securely deploy and manage cloud-native workloads—such as AI, Azure services, or your own business logic—to run directly on your IoT devices. Optimize cloud spend and enable your devices to react faster to local changes and operate reliably even in extended offline periods.

#### [What is Azure IoT Edge?](https://docs.microsoft.com/en-us/azure/iot-edge/about-iot-edge?view=iotedge-2020-11)
Azure IoT Edge is made up of three components:

-   **IoT Edge modules**  are containers that run Azure services, third-party services, or your own code. Modules are deployed to IoT Edge devices and execute locally on those devices.
-   The  **IoT Edge runtime**  runs on each IoT Edge device and manages the modules deployed to each device.
-   A  **cloud-based interface**  enables you to remotely monitor and manage IoT Edge devices.
- 
![Azure runtime](./assets/img/posts/20220724/Azure_runtime.png)

## 6. Baetyl (Baidu)
[Link:](https://baetyl.io/en/)



## 7. Link IoT edge (Aliyun)
[Link:](https://www.alibabacloud.com/zh/product/linkiotedge)

Link IoT Edge allows you to use TSL to convert devices of various protocols and data formats into standard TSL models. Link IoT Edge provides secure reliable low-latency cost-effective scalable weak-dependency local computing services. Link IoT Edge adopts Alibaba Cloud capabilities in several areas including security, storage, compute, and artificial intelligence (AI). You can deploy Link IoT Edge on intelligent devices and compute nodes at different levels of computing power. Link IoT Edge extends the boundary of Alibaba Cloud capability at the edge of your network.

![Link IoT Edge](./assets/img/posts/20220724/Link%20IoT%20Edge.png)

## 8. k3s
[Link:](https://k3s.io/) 

### Lightweight Kubernetes
The certified Kubernetes distribution built for IoT & Edge computing.

### Why use k3s?
##### Perfect for Edge
K3s is a highly available, certified Kubernetes distribution designed for production workloads in unattended, resource-constrained, remote locations or inside IoT appliances.

##### Simplified & Secure
K3s is packaged as a single <50MB binary that reduces the dependencies and steps needed to install, run and auto-update a production Kubernetes cluster.

##### Optimized for ARM
Both ARM64 and ARMv7 are supported with binaries and multiarch images available for both. K3s works great from something as small as a Raspberry Pi to an AWS a1.4xlarge 32GiB server.




