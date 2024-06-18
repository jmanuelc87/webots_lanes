# Webots Lanes Dataset

The csv files contain the next columns

 * imageFrontId : the front camera image
 * imageLeftId : the left camera image
 * imageRightId : the right camera image
 * steeringAngle : the general steering angle
 * leftSteeringAngle : the steering angle applied to the left wheel according to the ackerman geometry
 * rightSteeringAngle :  the steering angle applied to the right wheel according to the ackerman geometry
 * cruisingSpeed : the general speed of the vehicle
 * brakeIntensity : the brake intensity of the vehicle

# Project Modules

 * Perception Subsystem
 * Planning Subsystem
 * Control Subsystem

taken from [autonomous vehicle](https://sawhney-prateek97.medium.com/autonomous-vehicle-architecture-b802f30283fa)


# Interaction Between Modules

```mermaid
sequenceDiagram
    actor World
    participant Controller
    participant Perception Subsystem
    participant Planning Subsystem
    participant Control Subsystem


    World ->> Controller: (1) Takes images

    Controller ->> Perception Subsystem: Send images front, left, right
    Perception Subsystem ->> Perception Subsystem: Calculates steering angle and detects pedestrians and traffic signs
    Perception Subsystem -->> Controller: objects


    Controller ->> Planning Subsystem: Sends objects and radar targets
    Planning Subsystem ->> Planning Subsystem: Calculates trajectory
    Planning Subsystem -->> Controller: Steering angle, brake intensity, and speed


    Controller ->> Control Subsystem: Sends steering angle, brake intensity, and speed
    Control Subsystem ->> Control Subsystem: Control with PID
    Control Subsystem -->> Controller: Steering angle, brake intensity, and speed
```