# 🎭 IBDB Broadway shows Scraper

A Python-based web scraper that collects details about Broadway shows from [IBDB](https://www.ibdb.com/shows), saves them to CSV, detects new listings, and sends email notifications. Scheduled to run every 3 minutes.

---

## 📦 Features
- Scrapes show titles, types, opening/closing dates, image links, and performance counts
- Saves snapshots and maintains a master CSV
- Sends Gmail notifications for new shows
- Automatically runs every 3 minutes using `schedule`

---

## 🚀 Setup Instructions

### Prerequisites
- Python 3.8+
- Google Chrome + ChromeDriver
- Gmail app password for sending email

## 🧠 How It Works
### Scraper Logic
1. Launches Chrome using Selenium

2. Navigates to [https://www.ibdb.com/shows](https://github.com/Hykze1/Ticketmaster-webscrapping/blob/main/Ticketmaster.ipynb)

3. Parses the page with BeautifulSoup

4. Follows each show link to extract detailed data

5. Saves data into both timestamped and master CSV files

6. Compares against existing data to detect new entries

## 📁 Sample Output

![image](https://github.com/user-attachments/assets/21569cc0-ad0a-43a0-ac43-0ca7ae019a40)

## 📧 Email Notification Example
You’ll receive messages like:

Subject: New IBDB Shows Detected: 2 New Show(s)

- Funny Girl (Opening: Apr 24, 2025)
  
- Link: https://www.ibdb.com/show/funny-girl-2025



