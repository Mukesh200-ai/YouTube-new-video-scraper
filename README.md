# YouTube New Video Scraper Bot

* **Power Automate Desktop:** This tool is pre-installed on Windows 11 and is a free download for Windows 10. It can be used for free with any personal Microsoft account (like Outlook.com) or a work/school (Microsoft 365) account.

A Power Automate Desktop bot that scans a list of YouTube channels (from an Excel file) and creates a text file listing all videos posted within the last 24 hours.

This project is an advanced example of RPA, combining web scraping, data-driven loops, conditional logic, and file I/O.

## Features

* **Data-Driven:** Reads a list of channel URLs from an Excel file.
* **Smart Scraping:** Scrapes the "Videos" tab for each channel and extracts the Title, Upload Time, and Video Link.
* **Logic-Based:** Parses the "Upload Time" string (e.g., "5 hours ago", "22 minutes ago") to find only new content.
* **File Output:** Appends all newly found video titles and their full URLs to a single `YouTube_Finds.txt` output file.



---

## Prerequisites

To run this bot, you will need:
* Power Automate Desktop
* Microsoft Excel
* A compatible web browser (Edge/Chrome) with the Power Automate extension installed.
* A txt file to save output

---

## How to Set Up

### 1. Configure the Excel File

1.  Create an Excel file on your computer (e.g., `C:\My_Bots\channels.xlsx`).
2.  In the first row, create a single column header: `ChannelVideosURL`.
3.  In the rows below, paste the **full URLs** to the "Videos" tab of the channels you want to scan.
    * **Correct:** `https://www.youtube.com/@channel/videos`
    * **Incorrect:** `https://www.youtube.com/@channel`

### 2. Import the Bot

1.  Create a new, blank flow in Power Automate Desktop.
2.  Go to the `flow/` folder in this repository and open the `Main.flow` file in a text editor (like Notepad).
3.  Select all the text (`Ctrl+A`) and copy it (`Ctrl+C`).
4.  Paste this code (`Ctrl+V`) into the `Main` tab of your new flow.

### 3. Update File Paths

This is the most important step. The flow will not work until you update the hard-coded file paths to match your computer.

You **must** edit the following actions:

* **Launch Excel** (Action #1)
    * Update the `Document path` to point to your `channels.xlsx` file.
* **Write text to file** (Action #4)
    * Update the `File path` to where you want the `YouTube_Finds.txt` output file to be saved (e.g., `C:\My_Bots\YouTube_Finds.txt`).
* **Write text to file** (Action #16, inside the loop)
    * Update the `File path` to be the **exact same path** from the previous step.

* **The path you can paste directly in code**
    * Path 1 - Excel path - Line 1
    * Path 2 - txt file path - Line 5,11,15,18
  

### 4. Run the Bot

Run the flow. It will open a browser, scan each channel one by one, and then close. When it's finished, you can check your `YouTube_Finds.txt` file for the results.

---
