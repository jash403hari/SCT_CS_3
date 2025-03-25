# SCT_CS_3
# Import the Regular Expressions module for pattern matching
    import re  
    def assess_password_strength(password):
   """
    Function to assess the strength of a given password.

   Parameters:
    - password (str): The input password to evaluate.

  Output:
    - Prints the password strength rating.
    - Provides detailed criteria analysis.
    - Suggests improvements if necessary.
    """

  # === PASSWORD CRITERIA CHECKS ===
    length_criteria = len(password) >= 8  # Minimum 8 characters
    uppercase_criteria = re.search(r'[A-Z]', password)  # At least one uppercase letter
    lowercase_criteria = re.search(r'[a-z]', password)  # At least one lowercase letter
    letter_criteria = re.search(r'[A-Za-z]', password)  # At least one letter (any case)
    number_criteria = re.search(r'[0-9]', password)  # At least one digit
    special_char_criteria = re.search(r'[!@#$%^&*(),.?":{}|<>]', password)  # At least one special character

  # === CALCULATE PASSWORD SCORE ===
    score = sum([
        length_criteria,
        uppercase_criteria is not None,
        lowercase_criteria is not None,
        letter_criteria is not None,
        number_criteria is not None,
        special_char_criteria is not None
    ])

  # === ASSESS PASSWORD STRENGTH ===
    if score == 6 and len(password) >= 12:
        strength = "💪 Very Strong"
    elif score >= 5:
        strength = "✔️ Strong"
    elif score >= 4:
        strength = "⚠️ Moderate"
    else:
        strength = "❌ Weak"

  # === OUTPUT RESULTS ===
    print(f"\n🔒 Password Strength: {strength}\n")

    print("✅ Detailed Criteria Check:")
    print(f"- Length: {'✅ OK' if length_criteria else '❌ Too Short'}")
    print(f"- Uppercase Letter: {'✅ OK' if uppercase_criteria else '❌ Missing'}")
    print(f"- Lowercase Letter: {'✅ OK' if lowercase_criteria else '❌ Missing'}")
    print(f"- Any Letter: {'✅ OK' if letter_criteria else '❌ Missing'}")
    print(f"- Number: {'✅ OK' if number_criteria else '❌ Missing'}")
    print(f"- Special Character: {'✅ OK' if special_char_criteria else '❌ Missing'}")

# === SUGGESTIONS FOR IMPROVEMENT ===
    print("\n💡 Suggestions for a Stronger Password:")
    if not length_criteria:
        print("- 🔹 Use at least **8 characters** (12+ recommended for strong security).")
    if not uppercase_criteria:
        print("- 🔹 Include at least **one uppercase letter (A-Z)**.")
    if not lowercase_criteria:
        print("- 🔹 Include at least **one lowercase letter (a-z)**.")
    if not number_criteria:
        print("- 🔹 Add **at least one number (0-9)**.")
    if not special_char_criteria:
        print("- 🔹 Add **at least one special character (!@#$%^&*)**.")

# === USER INPUT ===
password = input("\n🔑 Enter a password to assess: ")
assess_password_strength(password)
