#TASK 1 WEEK 4

-my code is correct but I have problems in the output
#MY SCRIPT
--------------------------------------------------------
import openai
import speech_recognition as sr

# Function to capture speech input from the microphone
def capture_speech():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Say something...")
        audio = recognizer.listen(source)
        try:
            text = recognizer.recognize_google(audio)
            print(f"You said: {text}")
            return text
        except sr.UnknownValueError:
            print("Sorry, I could not understand the audio.")
            return None
        except sr.RequestError as e:
            print(f"Could not request results; {e}")
            return None

# Function to get response from OpenAI API
def get_openai_response(prompt):
    openai.api_key = '`sk-proj-5Dv4hK2117rX7CSTzksEAT3B1bkFJ1GDU1mgLk9aTgDJsqdze`'
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[
            {"role": "system", "content": "You are a helpful assistant."},
            {"role": "user", "content": prompt}
        ]
    )
    return response['choices'][0]['message']['content']

if __name__ == "__main__":
    user_input = capture_speech()
    if user_input:
        response = get_openai_response(user_input)
        print(f"ChatGPT response: {response}")
-----------------------------------------------
#OUTPUT

<img width="954" alt="image" src="https://github.com/user-attachments/assets/eb961df5-b61d-4744-80a5-fe4c5809d788">

<img width="782" alt="image" src="https://github.com/user-attachments/assets/5c1deaf2-291f-4a82-aa40-0aa5979020f9">













