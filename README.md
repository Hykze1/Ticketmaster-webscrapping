## 📄 IBDB Web Scraper

This Python script automatically scrapes Broadway show data from [IBDB.com](https://www.ibdb.com/shows), saves the data, and notifies you by email if new shows are detected.

---

### 🛠 How It Works – Step by Step

Even if you're not familiar with coding, here's what each part does:

1. **Launches a browser (automatically):**
   The script uses a tool called Selenium to open Chrome and go to the IBDB shows page.

2. **Finds show listings:**
   It waits until all the shows are visible, then grabs the HTML content of each show block.

3. **Extracts show info:**
   For each show (up to 40 max), it collects:

   * Show title
   * Show type (e.g., musical, play)
   * Opening and closing dates
   * Number of performances
   * Show detail page link
   * Image URL (poster)

4. **Saves the data:**
   The data is saved in two files:

   * A timestamped CSV for that scrape
   * A master CSV that tracks all shows ever scraped

5. **Detects new shows:**
   It compares the current scrape to the master CSV. If new shows appear, they’re identified and saved.

6. **Sends email notifications:**
   If new shows are found, an email is sent to notify you with the show titles and links.

---

### ⏰ How Scheduling Works

You don't need to run this manually each time.

At the bottom of the script:

```python
schedule.every(3).minutes.do(job)
```

This line sets the scraper to run **every 3 minutes**, automatically. It continuously checks for new shows.

How it works:

* The script starts running and never stops.
* Every 3 minutes, it scrapes, saves, and sends notifications.
* You’ll see logs in your terminal like:

  * `✅ Collected: Some Show`
  * `✅ Data saved to...`
  * `✅ Notification email sent.`

You can stop it anytime with `Ctrl + C`.

---

### 🔒 Anti-Scraping Precautions

Websites often try to block bots. Here’s what this script does to avoid detection:

1. **Waits for the page to fully load:**
   Uses `WebDriverWait` to avoid rushing the website, which can raise suspicion.

2. **Pauses between requests:**
   After scraping each show, the script pauses `1 second` with `time.sleep(1)`. This mimics human browsing.

3. **Only scrapes 40 shows max per run:**
   This avoids overloading the site with requests.

4. **Avoids crashing when elements are missing:**
   Errors like missing images or info won’t stop the whole script. Instead, it skips the problematic show and continues.

---

### 📦 Requirements to Run

Before running the script

Also:

* Make sure **Google Chrome** is installed
* Download the **ChromeDriver** that matches your browser version

  * [https://sites.google.com/chromium.org/driver](https://sites.google.com/chromium.org/driver)
  * Place it in the same folder or add it to your system PATH

---

### 📧 Email Notifications Setup

To receive emails:

* Use a Gmail account
* Enable [App Passwords](https://support.google.com/accounts/answer/185833?hl=en) and replace:

  ```python
  sender_password="your_app_password_here"
  ```
* Update these with your real emails:

  ```python
  sender_email="you@gmail.com"
  recipient_email="you@gmail.com"
  ```

---

## 📁 Sample Output

![image](https://github.com/user-attachments/assets/21569cc0-ad0a-43a0-ac43-0ca7ae019a40)

Saved to a folder called `data/`:

* `ibdb_master.csv` – full record of all shows
* `ibdb_shows_YYYYMMDD_HHMMSS.csv` – snapshot of each scrape


## 📧 Email Notification Example
You’ll receive messages like:

Subject: New IBDB Shows Detected: 2 New Show(s)

- Funny Girl (Opening: Apr 24, 2025)
  
- Link: https://www.ibdb.com/show/funny-girl-2025


---

### ✅ Summary

This script:

* Collects Broadway show data
* Saves and updates it locally
* Emails you when new shows appear
* Runs automatically every few minutes

---

