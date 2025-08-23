# mid-term-project-BQ-
this repo is for the mid term project for institute Bano Qabil



# Spam Email Detector with Simple Login
# Mid-term Project (Beginner Friendly)

# --- LOGIN SYSTEM FIRST ---
print("===== LOGIN SYSTEM =====")
username = input("Enter username: ")
password = input("Enter password: ")

# Simple login → any username/password works
print(f"\nWelcome {username}! Login Successful ✅")

# List of common spam keywords
spam_keywords = [
    "win", "free", "urgent", "prize", "lottery", "money", "offer", "click",
    "buy now", "limited time", "congratulations", "credit", "investment", "gift"
]

# Function to check spam score
def check_spam(email_text):
    email_text = email_text.lower()  # Convert to lowercase
    score = 0

    # Check spam keywords
    for word in spam_keywords:
        if word in email_text:
            score += 1

    # Check suspicious links
    words = email_text.split()
    for word in words:
        if word.startswith("http"):
            score += 2

    return score

# --- MAIN PROGRAM LOOP ---
while True:
    print("\n===== SPAM EMAIL DETECTOR =====")

    # User inputs email content
    email_content = input("\nPaste your email content here:\n")

    # Calculate spam score
    spam_score = check_spam(email_content)

    # Classification
    if spam_score >= 4:
        print("\nResult: This email is SPAM 🚫")
    elif spam_score >= 2:
        print("\nResult: This email looks Suspicious 🤔")
    else:
        print("\nResult: This email is Safe ✅")

    # Save result to file
    with open("spam_results.txt", "a") as file:
        file.write(f"Email: {email_content[:50]}...\nSpam Score: {spam_score}\n\n")

    print("\nAnalysis saved in 'spam_results.txt'")

    # Choice to continue or exit
    choice = input("\nDo you want to check another email? (yes/no): ").lower()
    if choice != "yes":
        print("\nThank you for using Spam Email Detector. Goodbye 👋")
        break
