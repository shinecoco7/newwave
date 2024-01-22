import time
from RPiSim.GPIO import GPIO

# Set up GPIO mode
GPIO.setmode(GPIO.BCM)

# Define motor pins
motor_pin1 = 17  # GPIO pin for motor control 1
motor_pin2 = 18  # GPIO pin for motor control 2

# Set GPIO pin directions
GPIO.setup(motor_pin1, GPIO.OUT)
GPIO.setup(motor_pin2, GPIO.OUT)

# Function to move the motor forward
def move_forward():
    GPIO.output(motor_pin1, GPIO.HIGH)
    GPIO.output(motor_pin2, GPIO.LOW)

# Function to move the motor backward
def move_backward():
    GPIO.output(motor_pin1, GPIO.LOW)
    GPIO.output(motor_pin2, GPIO.HIGH)

# Function to stop the motor
def stop_motor():
    GPIO.output(motor_pin1, GPIO.LOW)
    GPIO.output(motor_pin2, GPIO.LOW)

try:
    move_forward()
    print("Moving forward for 2 seconds")
    time.sleep(2)

    move_backward()
    print("Moving backward for 2 seconds")
    time.sleep(2)

    stop_motor()
    print("Motor stopped")

except KeyboardInterrupt:
    print("Exiting program")

finally:
    GPIO.cleanup()
