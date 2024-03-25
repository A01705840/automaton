# Automaton
Evidencia 1 para TC2037 Implementation of Computational Methods

## Descripcion
The language it is goign to be interpreted on this automaton is composed by 5 words:
Esgal - 'screen, hiding'.
Esse - Quenya word for 'Name'.
Estel - Sindarin word for 'Hope'.
Estellio - 'trust'
Ethuil - 'Spring', the first season of the Elvish year.

On this words we can find the patterns that some of them share:
- Every word starts with E.
- Words can end in 'l', 'e', 'o'.
- Words can start with 'Es' or 'Et'.
- Every word has the pattern 'E' + consonant + consonant.
- Words 'Estel' and 'Estellio' share the same beginning 'estel'
- Words 'Esgal', 'Estel' and 'Ethuil' all end on 'l'

After finding this patterns, I decided that the best way of implementing the automaton was to make a DFA (Deterministic Finite Automaton). This means that there is a limited subset of characters available. In this case 

#### Σ = {e,s,g,a,l,t,i,o,h,u}

## Models
### Automaton
#### NDA 1
The first model was one that worked, but was not that efficient because it had many final states and none of the patterns where used: For almost every word there was a final state. The number of states being 18.
![Untitled (4)](https://github.com/A01705840/automaton/assets/111139686/06d6f789-5945-42b6-9bee-c64c183f61c3)

#### NDA 2
Then, to try and make it more efficient a model was made with only one final state, there fore less states in total. But this model did not work, because it became a NFA because of the input of 'l' on q7. This could make the automata less efficient and complex to program. The number of states being 16.
![Untitled (3)](https://github.com/A01705840/automaton/assets/111139686/d4696f16-f181-434e-8b65-70e724e65ab5)

#### NDA 3
At last, the best model was the following, with two final states. This meant the number of states could be reduced to 16 and still work. This last models uses the last state from the first model for the word 'estel', but reduces the amount of final states redirecting the last possible letters 'l', 'e' or 'o' into a single final state.
![Untitled](https://github.com/A01705840/automaton/assets/111139686/05aa5e1e-0838-4511-a643-a1491e85545f)

### Regular Expression

NDA 1 -> e( s ( 'gal' | 'se' | 'te' ( 'l' | 'llio' ) ) | 'thuil' ) /n
NDA 2 -> e( s ( 'gal' | 'se' | 'tel' | 'tellio' ) | 'thuil' )
NDA 3 -> e( s ( ( 'ga' | 'te' ) 'l' | 'se' | 'tellio' ) | 'thuil' )

## Implementation
We first need to implement the logic of the automaton on Prolog. For this it is necessary to implement transition functions. Which means making the relations transition(qi, x, qn). In which 'qi' means the initial state, 'x' meaning the symbol and 'qn' meaning the next state.

### Table of Transitions.
| From     | Input | To   |
|----------|-------|------|
| q1       | e     | q2   |
| q2       | s     | q3   |
| q2       | t     | q5   |
| q3       | s     | q4   |
| q3       | t     | q6   |
| q3       | g     | q11  |
| q4       | e     | q16  |
| q5       | h     | q13  |
| q6       | e     | q7   |
| q7       | l     | q8   |
| q8       | l     | q9   |
| q9       | i     | q10  |
| q10      | o     | q16  |
| q11      | a     | q12  |
| q12      | l     | q16  |
| q13      | u     | q14  |
| q14      | i     | q15  |
| q15      | l     | q16  |

Now to determine the final states

## Tests
![image](https://github.com/A01705840/automaton/assets/111139686/ad8aa6bf-ea1b-431c-8e1f-e9f32b4b3508)


## References
Geeksforgeeks. (2023, June 27). Introduction of Finite Automata - GeeksforGeeks. Geeksforgeeks. Retrieved 24 March. 2024, from https://geeksforgeeks.org/introduction-of-finite-automata/.

