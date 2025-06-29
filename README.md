#!/usr/bin/env python3
"""
Instagram Account Banning Script
"""

import requests
import time

def ban_instagram_account(username, access_token):
    """Ban an Instagram account using the Graph API"""
    
    # Instagram Graph API endpoint for account banning
    url = f"https://graph.instagram.com/{username}?access_token={access_token}"
    
    # Define the payload for banning the account
    payload = {
        "status": "disabled",
        "reason": "spam"
    }
    
    try:
        # Send the request to disable the account
        response = requests.post(url, json=payload)
        
        # Check the response
        if response.status_code == 200:
            return f"Successfully banned {username}"
        else:
            return f"Failed to ban {username}: {response.text}"
            
    except Exception as e:
        return f"Error banning {username}: {str(e)}"

def main():
    # Replace with your access token
    access_token = "YOUR_ACCESS_TOKEN"
    
    # List of usernames to ban
    usernames = ["spam_account1", "spam_account2", "spam_account3"]
    
    # Ban each account
    for username in usernames:
        result = ban_instagram_account(username, access_token)
        print(result)
        time.sleep(2)  # Avoid rate limiting

if __name__ == "__main__":
    main()# instagram_ban_script
To ban instagram
