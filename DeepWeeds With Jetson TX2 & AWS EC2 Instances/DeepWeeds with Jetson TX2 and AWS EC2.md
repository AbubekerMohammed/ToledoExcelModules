# 🌿 DeepWeeds with Jetson TX2 and AWS EC2

## Overview

This educational module integrates the DeepWeeds deep learning application with both edge computing (Nvidia Jetson TX2) and cloud computing (AWS EC2) to teach students about parallel computing, GPU acceleration, and scalable deployment strategies. The goal is to provide hands-on experience with real-world tools and workflows in both edge and cloud contexts.

---

## DeepWeeds: Weed Species Classification

DeepWeeds is a deep learning-based image classification tool used to identify weed species using high-resolution imagery. Its GPU-intensive workload makes it ideal for demonstrating:
	•	GPU acceleration
	•	Data parallelism
	•	Optimized inference
	•	Cloud + Edge integration

Students deploy DeepWeeds on both AWS EC2 (cloud) and Jetson TX2 (edge) to evaluate performance trade-offs and understand deployment constraints.

---

## ☁️ AWS EC2 Cloud Deployment

Recommended Instance Configuration:
	•	Instance Type: p3.2xlarge
	•	GPU: NVIDIA V100 (16 GB GPU memory)
	•	CPU: 8 vCPUs
	•	RAM: 61 GB
	•	AMI: Deep Learning AMI (pre-configured)
	•	Cost: ~$3.06/hour

Launch Instance via CLI:

```bash
aws ec2 run-instances \
    --image-id ami-0123456789abcdef0 \
    --instance-type p3.2xlarge \
    --key-name student-key \
    --security-group-ids sg-0123456789abcdef0
```



---

## Auto Scaling Group (ASG) & Shared Storage (EFS)

To support multiple students simultaneously:
	•	ASG: Dynamically provisions EC2 instances on demand
	•	EFS: Enables shared access to datasets and model checkpoints

AWS CloudFormation Template:

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  DeepWeedsInstances:
    Type: 'AWS::EC2::LaunchTemplate'
    Properties:
      LaunchTemplateData:
        ImageId: ami-0c7217cdde317cfec
        InstanceType: p3.2xlarge
        SecurityGroupIds: 
          - sg-xxxxx

  AutoScalingGroup:
    Type: 'AWS::AutoScaling::AutoScalingGroup'
    Properties:
      MinSize: 1
      MaxSize: 10
      DesiredCapacity: 1
      LaunchTemplate:
        LaunchTemplateId: !Ref DeepWeedsInstances
```


---

## 🖥️ Jetson TX2 Edge Deployment
	•	CPU: ARM Cortex-A57
	•	GPU: Nvidia Pascal (256 CUDA cores)
	•	Toolkit: JetPack SDK (includes CUDA, cuDNN, TensorRT)

Drawbacks in Educational Context:
	•	Limited availability
	•	High cost per device
	•	Not scalable for large classrooms
	•	Best used optionally for advanced exploration

---

## 🛠️ Setup Instructions

Clone & Install:

```bash
git clone https://github.com/AlexOlsen/DeepWeeds.git
cd DeepWeeds

python3 -m venv deepweeds_env
source deepweeds_env/bin/activate

pip install -r requirements.txt
```

Key Python Requirements:

```text
tensorflow-gpu>=2.4.0
numpy>=1.19.2
opencv-python>=4.5.1
matplotlib>=3.3.3
pandas>=1.2.0
scikit-learn>=0.24.0
boto3>=1.17.78
awscli>=1.19.78
``

Run Models:

```bash
# ResNet50 Cross-Validation
python3 deepweeds.py cross_validate --model resnet

# Inference
python3 deepweeds.py inference --model models/resnet.hdf5
```



---

## 📋 Survey-Based Evaluation

Pre-Module Survey:

1. On a scale of 1-5, how familiar are you with parallel computing?
2. What programming languages are you proficient in?
3. Have you previously worked with cloud computing platforms? (Yes/No)
4. Describe your experience with ML frameworks.
5. Have you used GPU acceleration before? (Yes/No)

Post-Module Survey:

1. On a scale of 1-5, how well do you now understand parallel computing concepts?
2. How confident are you in using cloud platforms for ML?
3. Were the hands-on activities effective? (Yes/No)
4. Compare CPU vs. GPU after this exercise.
5. What would you improve in this module?
