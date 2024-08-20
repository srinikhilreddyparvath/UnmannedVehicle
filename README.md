# UnmannedVehicle
Design and implementation of Multi-Functional Autonomous vehicle
Agriculture and industrial sectors have been long physical task and labor extensive
areas. Indeed, even in India, these regions date back to before the Indus Valley Civilization and employ nearly half of the country’s population today, contributing 18 to 19
percent of the nation’s GDP. This can be substantially improved by combining traditional
farming techniques with modern electronic devices and IoT-based advancements.
The solution entails developing a model of independent automated transportation capabilities that is able to make farmers and workers life easy by removing the need for
labor and physical work for menial task. This includes but is not limited to smart transportation, carriage, smart farming, smart logistical solutions etc The solution combines
state of the art IOT advancement with modern day sensors all in a plug and play package.
Such a model can also create a vehicle that readily follows a path using object identification and line following. This vehicle can be used in processing plants, godowns,
healthcare facilities, emergency rooms, nurseries, mining, and other settings.
Physically controlled vehicles fall short of the standards of a project that aims for
independent control. Therefore, a step is taken forward by using node to node communication and a crucial setup of Arduino, Sensors, and Microcontrollers to work toward
developing a model that can independently move loads from one point to the next.
the models proposed can be utilised in many a sectors including agriculture and industrial. Line following capabilities find extensive usage in pre determined path works
such as those on working lands, factories or godowns. Hand following capabilities provide
logistical solutions for easy carriages of load in factories or Farms. Node to node communication vehicle can be used for all said cases but it also provides more control and
customisability the user with its application and functionalities it can perform. All in all
the 2 models proposed find extensive usecase in real world and helps to take India’s first
step towards electronic and IOT automation in farming agriculture and related sectors
The Existing models that are more than 100Kgs will now the Smaller with the ability
to carry more weight with no malfunction with respect to overheating. Automation has
come a huge step to resolve the existing problems that can be eradicated.

we used th basic code with yolov7:- 

import torch
import cv2
import numpy as np

# Load the YOLO model
model = torch.hub.load('ultralytics/yolov5', 'custom', path='best.pt')  

# Load the video feed (or a test image)
cap = cv2.VideoCapture(0)  

while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break

    # Perform detection
    results = model(frame)

    # Draw bounding boxes on the frame
    for *box, conf, cls in results.xyxy[0].tolist():
        label = f'{model.names[int(cls)]} {conf:.2f}'
        cv2.rectangle(frame, (int(box[0]), int(box[1])), (int(box[2]), int(box[3])), (255, 0, 0), 2)
        cv2.putText(frame, label, (int(box[0]), int(box[1]) - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.5, (255, 0, 0), 2)

    # Display the result
    cv2.imshow('Object Detection', frame)

    # Break loop with 'q'
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()

Project Focus:
My approach involves developing models that enable independent automated transportation, which can significantly ease the workload of farmers and workers by automating menial tasks. This includes creating smart solutions for transportation, carriage, farming, and logistics. My solution combines state-of-the-art IoT advancements with modern sensors, all packaged in a user-friendly, plug-and-play system.

Specific Contributions:
Object Identification: I am developing a machine learning model that enables the vehicle to identify objects such as crops, obstacles, and loading points. This involves using a convolutional neural network (CNN) model, like YOLOv5, which I’ve trained on a specific dataset relevant to the environment in which the vehicle will operate. This model will be deployed on an onboard computer or microcontroller that supports edge AI, ensuring real-time object detection.

Line Following: To enable the vehicle to navigate pre-determined paths, I am implementing a line-following system. I am considering both a PID controller for straightforward implementation and a neural network approach for more complex scenarios. The system uses sensor data, such as from IR sensors, to keep the vehicle on track in environments like farms or factories.

Node-to-Node Communication: Another aspect of my project involves setting up node-to-node communication using IoT protocols like MQTT or LoRa. This allows for coordination between multiple vehicles or between the vehicle and a central control station. I’m implementing ML algorithms to optimize this communication based on the environment and task requirements.

Real-World Applications:
The models I am developing have extensive real-world applications, ranging from agriculture to industrial settings like processing plants, godowns, healthcare facilities, and more. For example, the vehicle’s line-following capabilities are perfect for navigating pre-determined paths in factories or fields, while hand-following capabilities provide logistical solutions for easy load carriage. By leveraging node-to-node communication, I’m also ensuring that the system is highly customizable and adaptable to different tasks.

Innovation:
What sets my project apart is the focus on making these autonomous vehicles smaller, more efficient, and capable of carrying significant weight without issues like overheating. My work represents a significant step forward in electronic and IoT automation in farming, agriculture, and related sectors in India.

By integrating cutting-edge technologies like IoT, sensors, Arduino, and Microcontrollers, I’m not just improving efficiency but also contributing to the long-term sustainability of these vital sectors.

This project allows me to combine my technical expertise with a passion for social good, making a tangible impact on one of India's most critical industries.
