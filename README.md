import pyttsx3 #converts text to speech
import speech_recognition as sr
import webbrowser
import datetime
import pyjokes
import smtplib

def sptext():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source :
        print("plz say something")
        recognizer.adjust_for_ambient_noise(source)
        audio= recognizer.listen(source)
        try:
            print("recognizing...")
            data = recognizer.recognize_google(audio)
            
            return data #print(data)
        except sr.UnknownValueError :
            print("sorry cannot understand")

def tx2speech(x):
    engine = pyttsx3.init()
    voices = engine.getProperty('voices')
    engine.setProperty('voice',voices[1].id)
    rate = engine.getProperty('rate')
    engine.setProperty('rate',100)
    engine.say(x)
    engine.runAndWait()

if __name__ == '__main__':

    if sptext().lower() == "hii":
        data1 = sptext().lower()

        if "your name" in data1:
            name = "my name is Asish"
            tx2speech(name)
        elif "your age" in data1:
            age = "I am 20 years old"
            tx2speech(age)
        elif " time" in data1:
            time = datetime.datetime.now()
            tx2speech(time)
        elif 'youtube' in data1:
            url = webbrowser.open("https://www.youtube.com/channel/UCTbjfLvf4iS2sMq9eqGbV9g")
            
        elif 'google' in data1:
            url = webbrowser.open("https://www.google.co.in/")
        elif 'amazon' in data1 :
            url = webbrowser.open("https://www.amazon.in/")
        elif 'Gmail' in data1:
            url = webbrowser.open("https://mail.google.com/")
        else:
            print("say it again")
