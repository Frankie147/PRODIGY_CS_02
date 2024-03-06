import re

def check_password_strength(password):
    # Minimum length requirement
    min_length = 8

    # Regular expressions for different criteria
    has_uppercase = re.search(r'[A-Z]', password)
    has_lowercase = re.search(r'[a-z]', password)
    has_digit = re.search(r'\d', password)
    has_special_char = re.search(r'[!@#$%^&*(),.?":{}|<>]', password)

    # Calculate overall strength
    strength = 0

    if len(password) >= min_length:
        strength += 1

    if has_uppercase:
        strength += 1

    if has_lowercase:
        strength += 1

    if has_digit:
        strength += 1

    if has_special_char:
        strength += 1

    return strength

def main():
    password = input("Enter your password: ")
    strength = check_password_strength(password)

    if strength == 5:
        print("Password is very strong!")
    elif strength >= 3:
        print("Password is strong.")
    elif strength >= 2:
        print("Password is moderate.")
    elif strength >= 1:
        print("Password is weak.")
    else:
        print("Password is very weak. Please choose a stronger password.")

if __name__ == "__main__":
    main()
