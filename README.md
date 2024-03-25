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
![Untitled](https://github.com/A01705840/automaton/assets/111139686/05aa5e1e-0838-4511-a643-a1491e85545f)

### Regular Expression
e( s ( 'gal' | 'se' | 'te' ( 'l' | 'llio')) | 'thuil')

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

## Tests
![image](https://github.com/A01705840/automaton/assets/111139686/ad8aa6bf-ea1b-431c-8e1f-e9f32b4b3508)


## References
Geeksforgeeks. (2023, June 27). Introduction of Finite Automata - GeeksforGeeks. Geeksforgeeks. Retrieved 24 March. 2024, from https://geeksforgeeks.org/introduction-of-finite-automata/.

