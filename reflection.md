# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
Took a little time to load the input, the higher/lower hints were swapped and inaccurate, hint button has to be active in order to input and play the game which is wrong, 
- List at least two concrete bugs you noticed at the start  the higher/lower hints were swapped and inaccurate, hint button has to be active in order to input and play the game which is wrong, 
  (for example: "the secret number kept changing" or "the hints were backwards").

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
I used GitHub Copilot in VS Code for code suggestions, debugging, and generating tests.
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
The AI suggested removing the string conversion logic for the secret number to fix the inaccurate hints. I verified this by running the pytest tests, which all passed, and playing the game to confirm hints were now accurate.
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
Initially, the AI suggested keeping the show_hints checkbox but modifying the message display when hints were off. However, this still made the game unplayable without hints. I verified by testing the app and realizing users couldn't play effectively, so I removed the checkbox entirely.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
I decided a bug was fixed by running the pytest tests to ensure no regressions, and by manually playing the game to observe the behavior in the live app.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
I ran pytest on the test_game_logic.py file, which showed that all 5 tests passed, confirming the logic functions correctly. I also ran the Streamlit app and played a few rounds, verifying that hints were accurate and the score was visible.
- Did AI help you design or understand any tests? How?
Yes, the AI helped design the new test case for string secret handling by suggesting the test structure and assertions, which I then implemented and verified.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
The secret number kept changing because in the original code, it was only set if not in session_state, but due to Streamlit reruns on every interaction, the session_state was not persisting properly, or perhaps the logic was resetting it. Actually, in the fixed code, it persists, but the bug was the string conversion affecting comparisons.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Streamlit reruns the entire script every time the user interacts with the app, like clicking a button, which can reset variables unless you use session_state to store data across reruns. Session state is like a persistent dictionary that survives reruns, allowing you to keep track of things like user inputs or game state.
- What change did you make that finally gave the game a stable secret number?
I removed the conditional string conversion of the secret, ensuring it always remains an integer stored in session_state, which prevents comparison issues and keeps it stable.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
I want to reuse the habit of adding targeted test cases for specific bugs to ensure fixes are robust and prevent regressions.
- What is one thing you would do differently next time you work with AI on a coding task?
Next time, I would verify AI suggestions more thoroughly by testing edge cases before fully implementing, rather than assuming the first suggestion is complete.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
This project showed me that AI-generated code can have subtle bugs that require careful debugging, and that AI is a powerful tool for suggestions but human oversight is essential to ensure quality and correctness.
