# Vivy110
class AptosSocialNetwork:
    def __init__(self):
        # Initialize the database to store user accounts and posts
        self.user_accounts = {}
        self.posts = []

    def create_account(self, username):
        # Check if the username is already taken
        if username in self.user_accounts:
            return "Username already exists. Please choose a different one."

        # Create a new user account
        user_account = {
            "username": username,
            "posts": [],
        }

        # Store the user account in the database
        self.user_accounts[username] = user_account

        return f"Account for {username} created successfully."

    def post(self, username, content):
        # Check if the user account exists
        if username not in self.user_accounts:
            return f"Account with username {username} does not exist."

        # Create a new post
        post = {
            "username": username,
            "content": content,
            "comments": [],
            "likes": 0,
        }

        # Add the post to the user's account
        self.user_accounts[username]["posts"].append(post)
        # Add the post to the global posts list
        self.posts.append(post)

        return "Post published successfully."

# Example usage:
social_network = AptosSocialNetwork()
username = "mind slayer 3000"

result = social_network.create_account(username)
print(result)

content = "This is my first post!"
result = social_network.post(username, content)
print(result)
