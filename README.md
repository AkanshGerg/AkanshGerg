import speech_recognition as sr
import os

# Function to recognize voice commands
def recognize_command():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening for commands...")
        recognizer.adjust_for_ambient_noise(source)
        audio = recognizer.listen(source)

    try:
        # Recognize speech using Google Speech Recognition
        command = recognizer.recognize_google(audio).lower()
        print("You said: " + command)
        return command
    except sr.UnknownValueError:
        print("Could not understand audio")
    except sr.RequestError as e:
        print("Could not request results; {0}".format(e))

# Function to handle voice commands
def handle_command(command):
    if "hello" in command:
        print("Hello! How can I help you?")
    elif "play music" in command:
        os.system("start your_music_file.mp3")
    elif "open browser" in command:
        os.system("start chrome")
    elif "stop" in command:
        print("Stopping the program...")
        exit()
    else:
        print("Command not recognized.")

# Main function to listen for commands and handle them
def main():
    while True:
        command = recognize_command()
        handle_command(command)

if __name__ == "__main__":
    main()







