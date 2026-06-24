# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? 
  # The game looked fine when I first ran it except for the attempts allowed count.
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
  # The attempts left number is off and the target numbers were negative instead of in the range of 1 - 100

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input    | Expected Behavior | Actual Behavior | Console Output / Error |
|-------   |-------------------|-----------------|------------------------|
|guess of 0|  "Too low" hint   | "Too High" Hint |  None     
|new game  |  Game restart        Nothing           None
|score  number in between 1 - 100   negative number   None

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

# Correct AI Suggestion

The AI suggested moving the check_guess function from app.py into logic_utils.py to separate game logic from UI code. This suggestion was correct because it made the code easier to maintain and matched the goal of separating logic from the Streamlit interface.

I verified this by running pytest and confirming that all tests passed after the refactor. I also tested the game manually to confirm that Too High, Too Low, and Win responses worked correctly.

# Incorrect/Misleading AI Suggestion

The AI initially found that the old check_guess function used a try/except block that allowed string comparisons. This could have made it seem like the function needed to support strings, but that was actually hiding a bug.

I verified this by inspecting app.py and finding that the secret number was being converted into a string on even attempts. After removing that conversion, the game consistently compared numbers and the tests passed.

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I verified my fixes by creating pytest test cases for the game's guessing logic. I tested winning guesses, guesses above the secret number, and guesses below the secret number.

The command `pytest` was used to run the tests. The final result was:

4 passed in 0.04s

I also ran the Streamlit application and manually checked that the hints correctly instructed the player to go higher or lower.

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
