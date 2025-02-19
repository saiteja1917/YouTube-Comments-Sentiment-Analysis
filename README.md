# YouTube Comments Sentiment Analysis

## Overview

This project is designed to scrape YouTube comments from a specific video, analyze the sentiment of each comment using a machine learning model, and then save both the comments and their respective sentiment analysis results into CSV files. The project leverages the YouTube Data API and Hugging Face's `transformers` library to perform sentiment analysis.

## Features

- Scrape up to 100 comments from a YouTube video.
- Perform sentiment analysis on the scraped comments using the Hugging Face `pipeline` model.
- Save the comments to a CSV file.
- Save the sentiments and their scores to a separate CSV file.

## Requirements

The following Python packages are required:

- `google-auth`
- `google-auth-oauthlib`
- `google-auth-httplib2`
- `google-api-python-client`
- `pandas`
- `transformers`
- `torch`

You can install the required packages using the following command:
```bash
pip install google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client pandas transformers torch
```

## Setup

1. Clone the repository or download the project files.
2. Install the required Python packages (see above).
3. Obtain a YouTube API key from the [Google Cloud Console](https://console.cloud.google.com/).
4. Replace the placeholder in the code with your YouTube API key:
   ```python
   api_key = "YOUR_YOUTUBE_API_KEY"  # Replace with your YouTube API Key
   ```
5. Run the script in a Python environment.

## How to Run

1. Run the script using the following command:
   ```bash
   python script_name.py
   ```

2. The program will prompt you to input the YouTube video link:
   ```
   Paste the YouTube video link:
   ```

3. Once you provide the link, the script will:
   - Scrape the comments from the video.
   - Save the comments to a CSV file (`<video_id>_comments.csv`).
   - Analyze the sentiment of each comment.
   - Save the sentiments to another CSV file (`<video_id>_sentiments.csv`).

## Functionality

### `get_comments(video_id)`
- Scrapes up to 100 comments from a given YouTube video.
- Returns a list of comments.

### `save_comments_to_csv(comments, video_id)`
- Saves the list of comments into a CSV file named `<video_id>_comments.csv`.

### `analyze_sentiments(comments, max_length=512)`
- Analyzes the sentiment of each comment using the Hugging Face's `transformers` sentiment analysis pipeline.
- Optionally truncates comments longer than 512 characters to avoid input length issues.
- Returns a list of dictionaries containing the comment, sentiment, and sentiment score.

### `save_sentiments_to_csv(sentiments, video_id)`
- Saves the sentiment analysis results into a CSV file named `<video_id>_sentiments.csv`.

## Files

- **`script_name.py`**: The main script that scrapes comments, performs sentiment analysis, and saves the data to CSV files.
- **`requirements.txt`** (Optional): A file that can list the required dependencies for easier installation.

## Important Notes

- The API key provided must be a valid YouTube Data API key with permission to access YouTube data.
- Ensure that you respect YouTube's terms of service regarding API usage.
- This script only processes up to 100 comments per video, but you can extend it to scrape more by modifying the `maxResults` parameter and handling pagination in the API calls.

## Future Improvements

- Adding error handling for invalid video URLs.
- Extending the script to scrape more than 100 comments by continuously fetching the next pages.
- Option to provide a threshold to filter out comments with low sentiment scores.
- More detailed sentiment categorization beyond just positive, neutral, and negative.

## License

This project is licensed under the MIT License.
