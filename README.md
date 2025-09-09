<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 

<h3>Name: Shanmuga Vasanth M            </h3>

<h3>Register Number: 212223040191            </h3>

<H3>Aim:</H3>

<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>

<h2> Theory: </h2>

<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>

<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

<hr>

<h2> Program </h2>

```
import random
import string

def fitness(candidate, target):
    return sum(abs(ord(candidate[i]) - ord(target[i])) for i in range(len(target)))

def mutate(parent):
    idx = random.randrange(len(parent))
    new_char = random.choice(string.printable[:95])
    return parent[:idx] + new_char + parent[idx + 1:]

def hill_climb(target):
    current = ''.join(random.choice(string.printable[:95]) for _ in range(len(target)))
    current_score = fitness(current, target)
    while True:
        neighbor = mutate(current)
        neighbor_score = fitness(neighbor, target)
        if neighbor_score <= current_score:
            current, current_score = neighbor, neighbor_score
            print(f"Score: {current_score} Solution : {current}")
        if current_score == 0:
            break
    return current

target_string = "Artificial Intelligence"
solution = hill_climb(target_string)
print("\nFinal Solution:", solution)

```

<h2>Sample String:</h2>

Artificial Intelligence

<h2>Output:</h2>

<img width="888" height="407" alt="Screenshot 2025-09-09 204612" src="https://github.com/user-attachments/assets/c5695e99-9c85-4e11-9f7b-831de6ab167b" />

<img width="855" height="461" alt="image" src="https://github.com/user-attachments/assets/69c5ac1f-cb64-41ed-a9f9-be54141c6cb3" />

<h2> Result </h2>

Thus the program was executed successfully.
