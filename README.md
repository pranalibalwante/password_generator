# password_generator
import random
import string


def generate_password(length):
    if length < 4:  # Ensure the length is at least 4 to include all character types
        print("Password length should be at least 4.")
        return None

    # Define character sets
    all_characters = string.ascii_letters + string.digits + string.punctuation

    # Ensure the password contains at least one character from each set
    password = [
        random.choice(string.ascii_lowercase),
        random.choice(string.ascii_uppercase),
        random.choice(string.digits),
        random.choice(string.punctuation)
    ]

    # Fill the rest of the password length with random characters from all_characters
    password += random.choices(all_characters, k=length - 4)

    # Shuffle the password list to ensure randomness
    random.shuffle(password)

    # Convert the list to a string and return
    return ''.join(password)


def main():
    try:
        length = int(input("Enter the desired length for the password: "))
    except ValueError:
        print("Invalid input. Please enter a numeric value.")
        return

    password = generate_password(length)
    if password:
        print(f"Generated Password: {password}")


if __name__ == "__main__":
    main()
