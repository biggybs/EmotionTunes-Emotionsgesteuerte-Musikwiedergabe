# EmotionTunes-Emotionsgesteuerte-Musikwiedergabe
EmotionTunes passt die Wiedergabeliste automatisch an die Stimmung des Hörers an, indem es dessen Emotionen durch Gesichtserkennung und Biofeedback erfasst und entsprechende Musik auswählt.
import cv2
from deepface import DeepFace
import os
import random

# Assume a predefined dictionary of music tracks categorized by emotion
music_by_emotion = {
    "happy": ["happy_song1.mp3", "happy_song2.mp3"],
    "sad": ["sad_song1.mp3", "sad_song2.mp3"],
    "angry": ["angry_song1.mp3", "angry_song2.mp3"],
    "neutral": ["neutral_song1.mp3", "neutral_song2.mp3"],
    # Add more emotions as needed
}

def detect_emotion_from_image(image_path):
    """
    Detects the dominant emotion from a given image.
    """
    analysis = DeepFace.analyze(img_path = image_path, actions = ['emotion'], enforce_detection=False)
    return analysis["dominant_emotion"]

def play_music_for_emotion(emotion):
    """
    Selects and "plays" a music track based on the detected emotion.
    Replace print statement with actual code to play music.
    """
    if emotion in music_by_emotion:
        song = random.choice(music_by_emotion[emotion])
        print(f"Playing {song} for emotion: {emotion}")
    else:
        print("No songs found for this emotion.")

def main():
    image_path = "path/to/your/image.jpg"  # Change this to the path of your image
    emotion = detect_emotion_from_image(image_path)
    print(f"Detected emotion: {emotion}")
    play_music_for_emotion(emotion)

if __name__ == "__main__":
    main()
