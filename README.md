
# Cumul.io AI-powered Dashboard Generator

This Node.js script connects to your Cumul.io account to listen for new datasets added, and generates dashboards based on the dataset metadata in your Cumul.io account using the OpenAI API. The generated dashboards are then created in your Cumul.io account.

This Cumul.io Blog post goes into detail on how this script works and what to expect as output: [https://www.cumul.io/blog/ai-powered-dashboards-tutorial](https://www.cumul.io/blog/ai-powered-dashboards-tutorial).

## Prerequisites

Before running the script, make sure you have the following:

-   A Cumul.io account (you can start a  [free 10-day trial](https://app.cumul.io/signup))
-   An OpenAI account (you can  [create a free account](https://platform.openai.com/)  and API key, which gives you $18 in credit to experiment, more than enough for this demo)

## Installation

1. Clone this repository or download the script file to your local machine.

2. Install the required dependencies by running the following command:

   ```bash
   npm install
   ```
Set up environment variables by creating a .env file in the project directory and providing the necessary credentials. The .env file should contain the following variables:

```dotenv
CUMULIO_API_HOST_URL=<Cumul.io API host URL>
CUMULIO_API_KEY=<Cumul.io API key>
CUMULIO_API_SECRET=<Cumul.io API token>
OPENAI_API_SECRET=<OpenAI API key>
```
Replace `<Cumul.io API host URL>` (typically `https://api.cumul.io` or `https://api.us.cumul.io`), `<Cumul.io API key>`, `<Cumul.io API token>`, and `<OpenAI API key>` with your actual credentials.


## Usage
To run the script, use the following command:

```bash
node .
```
The script will start listening for new datasets in Cumul.io (it will first print all currently accessible dataset IDs). Every five seconds, it will check for new datasets and pass their metadata (dataset name and column names) to the OpenAI API along with a proposed JSON structure for generating the six most relevant charts based on the dataset metadata.

The OpenAI API will return a response containing the generated dashboard configuration in JSON format. The script will then create the dashboard in your Cumul.io account.