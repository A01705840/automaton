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
- Words can end in l, e, o.
- Words can start with Es or Et.
- Every word has the pattern E + consonant + consonant.
- Words 'Estel' and 'Estellio' share the same beginning 'estel'
- Words 'Esgal', 'Estel' and 'Ethuil' all end on 'l'

After finding this patterns, I decided that the best way of implementing the automaton was to make a DFA (Deterministic Finite Automaton). This means that there is a limited subset of characters available. In this case 

#### Σ = {e,s,g,a,l,t,i,o,h,u}

## Models
![Untitled](https://github.com/A01705840/automaton/assets/111139686/05aa5e1e-0838-4511-a643-a1491e85545f)
