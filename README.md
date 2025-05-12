# Kinetik8
#Armbot with 7 motors, 2 step motors and 5 servomotors controled by a Raspberry pi Zero 2W and Arduino Mega2560, the project have two sensors modules, a strain gauge and infra-red optical sensor.
#this project use a power supply with 24VDC 16.6A, have two DC-DC Converter, four fuse, 19 leds, PID control.
#The Raspberry Pi Zero 2W is responsible for the entire system in the robotic arm. The Mega2560 handles sending PWM signals to the motors, but it operates as a slave while the Raspberry Pi acts as the master UART

def move_servo(servo_id, angle):
    command = f"S,{servo_id},{angle}"
    return send_command(command)

def move_stepper(stepper_id, steps, direction):
    command = f"M,{stepper_id},{steps},{direction}"
    return send_command(command)

def get_distance():
    return send_command("D")

def get_force():
    return send_command("F")

print(move_servo(1, 90))  # Mueve el servo 1 a 90°
print(move_stepper(1, 200, 1))  # Mueve el motor paso a paso 1, 200 pasos adelante
print("Distancia:", get_distance())  # Muestra la distancia medida
print("Fuerza:", get_force())  # Muestra la fuerza medida por la galga

arduino.close()

