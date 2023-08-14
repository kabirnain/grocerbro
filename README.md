# grocerbro
Python-based chatbot with advanced keyword matching function


**Keyword Lists:**
The chatbot uses predefined lists of keywords to identify and categorize user input. These lists include:

**recipe_keywords:** Keywords related to recipes.
**ingridient_keywords:** Keywords related to individual ingredients.
**cart_keywords, checkout_keywords, recipe_list_keywords, etc.:** Keywords related to various chatbot actions like viewing the cart, checking out, viewing a list of recipes, and more.

**Keyword Matching Mechanism:**

The chatbot's keyword matching mechanism works as follows:

**User Input Tokenization:** When the user provides input, the chatbot breaks it down into individual words or tokens.

**Matching with Keyword Lists:** The chatbot checks each token against the predefined keyword lists to determine which category or action the user's input matches.

**Count Matching Keywords:** For each potential action (like viewing recipes, adding ingredients to cart, etc.), the chatbot counts the number of keywords in the user's input that match that action's keyword list.

**Determine Best Match:** The chatbot determines the action with the highest count of matching keywords as the best match. This action is then executed. If there's a tie or no clear match, the chatbot might use a default action or ask the user for clarification.

**Implementation in the Code:**
The function categorize_call(user_input) is responsible for categorizing user input based on keyword matches.

**Inside categorize_call, the chatbot:**

Uses the function list_to_dict to create a dictionary with keywords as keys and initial counts set to zero.
Calls the function match_master(user_input, keyword_dict) to identify matching keywords from the user's input.
For each potential action in action_dict, the chatbot counts the number of matching keywords and updates the action's counter.
After checking all actions, the action with the highest counter is identified as the best match.
The dictionary action_dict maps potential actions to their corresponding keyword lists and functions. For example, if the best match is found_recipe, the chatbot will execute the function associated with viewing or adding a recipe.

**Example:**
Let's say the user types "I want a recipe for tacos."

The chatbot tokenizes this to: **["I", "want", "a", "recipe", "for", "tacos"]**
It checks each token against the predefined keyword lists.
The words "recipe" and "tacos" match the recipe_keywords list.
If no other action has a higher keyword match count, the chatbot identifies this input as a request to view a taco recipe.
By using this keyword matching mechanism, the chatbot can understand and categorize a wide range of user inputs, even if the phrasing varies. However, it's worth noting that this approach has its limitations and might not handle complex or ambiguous queries as effectively as more advanced natural language processing techniques.
