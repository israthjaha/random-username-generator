# random-username-generator
import random

def generate_username(adjectives, nouns, include_numbers=False, include_special_chars=False, length=None):
    username = random.choice(adjectives) + random.choice(nouns)
    
    if include_numbers:
        username += str(random.randint(1, 999))
    
    if include_special_chars:
        special_chars = ['!', '@', '#', '$', '%', '^', '&', '*']
        username += random.choice(special_chars)
    
    if length and len(username) > length:
        username = username[:length]
    
    return username

def save_usernames_to_file(usernames, filename='usernames.txt'):
    with open(filename, 'w') as file:
        for username in usernames:
            file.write(username + '\n')

def main():
    adjectives = ['Cool', 'Happy', 'Brave', 'Silly', 'Clever']
    nouns = ['Tiger', 'Dragon', 'Panda', 'Ninja', 'Wizard']
    
    num_usernames = int(input("How many usernames would you like to generate? "))
    include_numbers = input("Include numbers? (yes/no): ").strip().lower() == 'yes'
    include_special_chars = input("Include special characters? (yes/no): ").strip().lower() == 'yes'
    length = input("Specify maximum length of usernames (press enter for no limit): ")
    length = int(length) if length.isdigit() else None
    
    generated_usernames = set()
    
    while len(generated_usernames) < num_usernames:
        username = generate_username(adjectives, nouns, include_numbers, include_special_chars, length)
        generated_usernames.add(username)
print("Generated Usernames:")
    for username in generated_usernames:
        print(username)
    
    save_usernames_to_file(generated_usernames)

if _name_ == "_main_":
    main()
