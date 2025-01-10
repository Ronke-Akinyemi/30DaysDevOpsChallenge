
# 30 Days DevOps Challenge - Weather Dashboard
Day 1: Building a weather data collection system using AWS S3 and OpenWeather API


## Project Overview
The Weather Dashboard is a Python-based project that fetches real-time weather data for different cities from the OpenWeather API and securely stores it in AWS S3. It provides detailed weather information such as temperature, humidity, and conditions, demonstrating the integration between APIs and cloud services using Python.


## Technologies Used
- Python 3.12
- AWS S3 for cloud storage
- boto3 for AWS integration
- requests for API calls
- python-dotenv for environment variable management

## Prerequisites
- Python 3.12 or higher installed.
- An AWS account with permissions to create and manage S3 buckets.
- An OpenWeather API key.

## Setup
- Clone the repository
- git clone https://github.com/Ronke-Akinyemi/30DaysDevOpsChallenge.git
- cd weather-dashboard

## Install dependencies
- python3 -m pip install -r requirements.txt

## Create a .env file in the project root and add the following:
- OPENWEATHER_API_KEY=your_openweather_api_key
- AWS_BUCKET_NAME=your_bucket_name

## Run the script:
- python3 weather_dashboard.py
