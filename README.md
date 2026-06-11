# thiranex_password
import re

password = input("Enter Password: ")

score = 0
suggestions = []

# Check length
if len(password) >= 8:
    score += 1
else:
    suggestions.append("Password should be at least 8 characters long.")

# Check uppercase letter
if re.search(r"[A-Z]", password):
    score += 1
else:
    suggestions.append("Add at least one uppercase letter (A-Z).")

# Check lowercase letter
if re.search(r"[a-z]", password):
    score += 1
else:
    suggestions.append("Add at least one lowercase letter (a-z).")

# Check number
if re.search(r"\d", password):
    score += 1
else:
    suggestions.append("Add at least one number (0-9).")

# Check special character
if re.search(r"[!@#$%^&*(),.?\":{}|<>]", password):
    score += 1
else:
    suggestions.append("Add at least one special character (@,#,$,etc.).")

# Determine strength
if score <= 2:
    strength = "Weak Password"
elif score <= 4:
    strength = "Medium Password"
else:
    strength = "Strong Password"

print("\nPassword Strength:", strength)

# Display suggestions
if suggestions:
    print("\nSuggestions to Improve Password:")
    for suggestion in suggestions:
        print("-", suggestion)
else:
    print("\nExcellent! Your password is very secure.")
