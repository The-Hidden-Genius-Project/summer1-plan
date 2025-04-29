# Weeks 6-7: Debug Like a Pro & Fun Project Integration

## Week 6: Debugging Fundamentals & Project Implementation
---
## Day 1: Introduction to Debugging & Error Types
### Session Duration
- **Python Session**: 120 minutes
- **HTML/CSS Session**: 60 minutes

### Session Objectives
By the end of the session, students will:
- Understand different types of errors
- Master basic debugging techniques
- Implement odd_or_even game
- Style interactive elements

### Materials Needed
- Debugging cheat sheet
- Error type reference
- VS Code debugger guide
- Sample broken code
- Project templates

### Python Session Plan (120 minutes)
1. **Understanding Errors** (45 minutes)
   - **Types of Errors** (20 minutes)
     - Syntax errors
     - Logic errors
     - Runtime errors
     ```python
     # Common error examples
     # Syntax Error
     print "Hello"  # Missing parentheses
     
     # Logic Error
     def add_numbers(a, b):
         return a - b  # Wrong operator
     
     # Runtime Error
     numbers = [1, 2, 3]
     print(numbers[5])  # Index error
     ```
   - **Error Messages** (25 minutes)
     - Reading tracebacks
     - Understanding error messages
     - Common error patterns

2. **Project: Odd or Even Game** (45 minutes)
   ```python
   def odd_or_even_game():
       """
       Interactive game testing number properties
       and handling user input
       """
       import random
       score = 0
       rounds = 5

       print("Welcome to Odd or Even!")
       print("I'll show you a number, you tell me if it's odd or even.")
       
       for round in range(rounds):
           number = random.randint(1, 100)
           print(f"\nNumber: {number}")
           
           guess = input("Is this number odd or even? ").lower()
           correct_answer = "even" if number % 2 == 0 else "odd"
           
           if guess == correct_answer:
               score += 1
               print("Correct! 🎉")
           else:
               print(f"Sorry, {number} is {correct_answer}!")
               
       print(f"\nGame Over! You got {score} out of {rounds} correct!")
   ```

3. **Debug Practice** (30 minutes)
   - Finding bugs in the game
   - Implementing error handling
   - Adding input validation

### HTML/CSS Session Plan (60 minutes)
1. **Interactive Elements** (30 minutes)
   - Button states
   - Input validation
   - Error messages

2. **Game Interface** (20 minutes)
   - Score display
   - Round counter
   - Feedback elements

3. **Review & Enhancement** (10 minutes)
   - Testing
   - User feedback
   - Improvements

### Assessment & Reflection
- Error identification quiz
- Debugging exercises
- Game implementation
- Interface design

### Homework Assignment
- Debug practice problems
- Enhance odd_or_even game
- Add more features
- Style improvements

---
## Day 2: Common Bug Patterns & Countdown Timer
### Session Duration
- **Python Session**: 120 minutes
- **HTML/CSS Session**: 60 minutes

### Session Objectives
By the end of the session, students will:
- Identify common bug patterns
- Create countdown timer
- Implement timer interface
- Add animations

### Python Session Plan (120 minutes)
1. **Common Bug Patterns** (45 minutes)
   - **Pattern Recognition** (20 minutes)
     - Off-by-one errors
     - Infinite loops
     - Variable scope issues
   - **Pattern Solutions** (25 minutes)
     - Debug strategies
     - Prevention techniques
     - Best practices

2. **Project: Countdown Timer** (45 minutes)
   ```python
   import time
   
   def countdown_timer():
       """
       Interactive countdown timer with
       visual and sound feedback
       """
       def format_time(seconds):
           minutes = seconds // 60
           remaining_seconds = seconds % 60
           return f"{minutes:02d}:{remaining_seconds:02d}"
   
       def validate_input(user_input):
           try:
               minutes = int(user_input)
               if minutes <= 0 or minutes > 60:
                   raise ValueError
               return minutes
           except ValueError:
               return None
   
       while True:
           user_time = input("Enter minutes to countdown (1-60): ")
           minutes = validate_input(user_time)
           
           if minutes:
               total_seconds = minutes * 60
               break
           print("Please enter a valid number between 1 and 60")
   
       print("\nCountdown starting!")
       for remaining in range(total_seconds, -1, -1):
           print(f"\r{format_time(remaining)}", end="")
           time.sleep(1)
           
       print("\nTime's up! 🎉")
   ```

3. **Enhancement & Debug** (30 minutes)
   - Add pause/resume
   - Implement sound
   - Error handling

### HTML/CSS Session Plan (60 minutes)
1. **Timer Interface** (30 minutes)
   - Digital display
   - Control buttons
   - Progress indicator

2. **Animation Effects** (20 minutes)
   - Countdown animation
   - Completion effects
   - Sound integration

3. **Testing & Review** (10 minutes)
   - Browser testing
   - Performance check
   - User feedback

---
## Day 3: Advanced Debugging & Hangman Game
### Session Duration
- **Python Session**: 120 minutes
- **HTML/CSS Session**: 60 minutes

### Session Objectives
By the end of the session, students will:
- Use advanced debugging tools
- Create Hangman game
- Design game interface
- Implement keyboard input

### Python Session Plan (120 minutes)
1. **Advanced Debugging** (45 minutes)
   - **VS Code Debugger** (20 minutes)
     - Breakpoints
     - Watch variables
     - Step through code
   - **Debug Strategies** (25 minutes)
     - Print debugging
     - Logging
     - Exception handling

2. **Project: Hangman** (45 minutes)
   ```python
   import random
   
   class Hangman:
       def __init__(self):
           self.words = ['python', 'javascript', 'programming', 'computer', 'algorithm']
           self.word = random.choice(self.words)
           self.guessed_letters = set()
           self.max_tries = 6
           self.tries = 0
   
       def display_word(self):
           return ' '.join(letter if letter in self.guessed_letters 
                         else '_' for letter in self.word)
   
       def make_guess(self, letter):
           if letter in self.guessed_letters:
               return "You already guessed that letter!"
           
           self.guessed_letters.add(letter)
           if letter not in self.word:
               self.tries += 1
               return f"Wrong guess! {self.max_tries - self.tries} tries left!"
           
           if all(letter in self.guessed_letters for letter in self.word):
               return "Congratulations! You won! 🎉"
           
           return "Good guess!"
   
       def play(self):
           print("Welcome to Hangman!")
           print(f"The word has {len(self.word)} letters.")
           
           while self.tries < self.max_tries:
               print(f"\nWord: {self.display_word()}")
               print(f"Guessed letters: {', '.join(sorted(self.guessed_letters))}")
               
               guess = input("Guess a letter: ").lower()
               if len(guess) != 1:
                   print("Please enter a single letter!")
                   continue
                   
               result = self.make_guess(guess)
               print(result)
               
               if "Congratulations" in result:
                   break
                   
           if self.tries >= self.max_tries:
               print(f"\nGame Over! The word was: {self.word}")
   ```

3. **Game Enhancement** (30 minutes)
   - Add word categories
   - Implement hints
   - Score tracking

### HTML/CSS Session Plan (60 minutes)
1. **Game Interface** (30 minutes)
   - Word display
   - Keyboard layout
   - Hangman visualization

2. **Interactive Elements** (20 minutes)
   - Key press handling
   - Visual feedback
   - Win/lose animations

3. **Testing & Polish** (10 minutes)
   - Game flow
   - Error handling
   - User experience

---
## Day 4: Project Integration & Bug Hunt
### Session Duration
- **Python Session**: 120 minutes
- **HTML/CSS Session**: 60 minutes

### Project: Game Collection Platform
Students will integrate all three games (Odd or Even, Countdown Timer, Hangman) into a single platform with shared scoring and user tracking.

### Python Session Plan (120 minutes)
1. **Project Structure** (30 minutes)
   ```python
   class GamePlatform:
       def __init__(self):
           self.player_name = ""
           self.total_score = 0
           self.games = {
               '1': ('Odd or Even', self.play_odd_or_even),
               '2': ('Countdown Timer', self.play_countdown),
               '3': ('Hangman', self.play_hangman)
           }
   
       def main_menu(self):
           print("\n=== Game Platform ===")
           print(f"Player: {self.player_name}")
           print(f"Total Score: {self.total_score}")
           print("\nAvailable Games:")
           for key, (game_name, _) in self.games.items():
               print(f"{key}. {game_name}")
           print("4. View Stats")
           print("5. Exit")
   ```

2. **Integration** (60 minutes)
   - Game selection system
   - Score tracking
   - Statistics storage

3. **Enhancement** (30 minutes)
   - Leaderboard
   - Achievements
   - Progress tracking

### HTML/CSS Session Plan (60 minutes)
1. **Platform Interface** (30 minutes)
   - Game selection
   - Score display
   - Navigation

2. **Final Polish** (20 minutes)
   - Transitions
   - Responsive design
   - Cross-browser testing

3. **Launch Prep** (10 minutes)
   - Final testing
   - Documentation
   - Deployment

### Key Learning Integration
- Variables & Data Types
  - Score tracking
  - Player information
  - Game states

- Functions & Control Flow
  - Game logic
  - Input validation
  - State management

- Lists & Dictionaries
  - Word lists
  - Game options
  - Statistics tracking

- String Operations
  - Display formatting
  - Input processing
  - Message handling

- Git & Version Control
  - Feature branches
  - Merge management
  - Deployment process

### Debugging Focus Areas
1. **Input Validation**
   - Type checking
   - Range validation
   - Error messages

2. **State Management**
   - Game progress
   - Score tracking
   - User sessions

3. **Error Handling**
   - Invalid inputs
   - Edge cases
   - Graceful failures

4. **Performance**
   - Animation smoothness
   - Load times
   - Resource usage

### Extension Ideas
1. **Additional Games**
   - Number guessing
   - Word scramble
   - Memory match

2. **Enhanced Features**
   - Multiplayer support
   - Custom word lists
   - Difficulty levels

3. **Social Features**
   - Global leaderboard
   - Achievement sharing
   - Friend challenges
