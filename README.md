# FarMart-

# Problem
We have a huge log file (1 TB in size) with logs for multiple years. Each log starts with a date in the format YYYY-MM-DD. The task is to extract all logs for a specific date efficiently without loading the entire file into memory.

Solution Steps

# Approach
- **Indexing:** Create an index that maps dates to byte offsets in the file. This allows us to jump directly to the relevant part of the file.
- **Binary Search:** Use binary search to quickly locate the start and end positions of the logs for the specified date.
- **Streaming:** Read the file in chunks to avoid loading the entire file into memory.


Create an Index:
The script scans the log file once and creates an index.
The index maps each date (e.g., 2024-12-01) to its starting position (byte offset) in the file.
This index is saved to a file (log_index.txt) so we don’t need to scan the log file again.
Load the Index:
When you run the script, it loads the index from log_index.txt into memory.
This allows the script to quickly find where logs for a specific date start in the file.
Extract Logs:
The script uses the index to jump directly to the logs for the specified date.
It reads the file from that position and collects all logs for the date.
It stops when it finds logs for the next date.
Save the Logs:
The extracted logs are saved to a file in the output folder, named output_YYYY-MM-DD.txt.
How It Works

First Run:
The script scans the log file to create the index (this takes some time but only needs to be done once).
It then extracts logs for the specified date and saves them to the output file.
Subsequent Runs:
The script uses the existing index to quickly find and extract logs for any date.

Why It’s Efficient

Saves Time: No need to scan the entire file every time.

Saves Memory: Processes the file in chunks, so it works even on machines with limited RAM.

Easy to Use: Just provide the date, and the script does the rest.
