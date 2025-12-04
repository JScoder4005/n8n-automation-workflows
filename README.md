# n8n Daily Weather Bot Setup

This guide will help you set up your daily weather bot using n8n, OpenWeatherMap, and WhatsApp.

## Prerequisites

1.  **n8n Installed**: You need a running instance of n8n (Desktop app, Docker, or Cloud).
2.  **OpenWeatherMap API Key**: Sign up at [openweathermap.org](https://openweathermap.org/) to get a free API key.
3.  **Meta for Developers Account**: You need a Meta account to use the WhatsApp Cloud API.
    *   Go to [developers.facebook.com](https://developers.facebook.com/).
    *   Create a new app (Type: Business).
    *   Add the **WhatsApp** product to your app.
    *   Get your **Phone Number ID** and **Permanent Access Token** (or use the temporary one for testing).
    *   Add your own phone number as a **Recipient** in the test section.

## Installation

1.  **Import Workflow**:
    *   Open your n8n dashboard.
    *   Click on the menu (top right) -> **Import from File**.
    *   Select the `weather-workflow.json` file provided in this folder.

2.  **Configure Credentials**:
    *   **OpenWeatherMap Node**:
        *   Double-click the "OpenWeatherMap" node.
        *   Under "Credentials", select "Create New".
        *   Enter your OpenWeatherMap API Key.
    *   **WhatsApp Node**:
        *   Double-click the "WhatsApp" node.
        *   Under "Credentials", select "Create New".
        *   Enter your **Access Token** and **Business Account ID** from the Meta dashboard.
        *   In the node parameters, enter your **Phone Number ID** (from Meta) and the **Recipient Phone Number** (your number, with country code, e.g., `919876543210`).

3.  **Test**:
    *   Click the **Execute Workflow** button at the bottom of the canvas.
    *   Check your WhatsApp! You should receive the weather message.

4.  **Activate**:
    *   Once tested, toggle the **Active** switch in the top right corner to enable the daily schedule (8:00 AM).

## Troubleshooting

*   **No Message?**: Check the "Executions" tab in n8n for errors.
*   **WhatsApp Error?**: Ensure you have messaged the bot number first if using the test sandbox, or that you are using a valid template if outside the 24-hour window (though for testing, replying to the bot usually opens the window).
