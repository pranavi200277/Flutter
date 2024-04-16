import time
import winsound

reminders = {
    "Wake up": 7,
    "Go to gym": 8,
    "Breakfast": 9,
    "Meetings": 10,
    "Lunch": 12,
    "Quick nap": 14,
    "Go to library": 16,
    "Dinner": 18,
    "Go to sleep": 22
}

def play_sound():
    winsound.Beep(1000, 1000) 
    
if __name__ == "__main__":
    day = input("Enter the day of the week: ")
    print("Enter the time for each activity in 24-hour format (e.g., 7 for 7 AM, 13 for 1 PM)")

    while True:
        current_time = time.localtime()
        current_hour = current_time.tm_hour
        current_day = time.strftime("%A", current_time)

        if current_day.lower() == day.lower() and current_hour in reminders.values():
            for activity, hour in reminders.items():
                if current_hour == hour:
                    print(f"It's time to {activity.lower()}!")
                    play_sound()
                    time.sleep(60)  
                    break
        else:
            time.sleep(60)  
