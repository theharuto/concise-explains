```markdown
19/1/26
- sealed classes are used to restirct the inheritance hierarchy while also allowing extension points ( sealed, final , non-sealed)
use abstract to define the method contract and let the subclasses implement their own business logic
use enum or returning string for fixed set of values

- switch expression : can return values, allows null (must handle null case explicitly), allows unnamed variables and pattern
matching
- unnamed variables : if you don't use it then don't name it.
```
```
20/1/26
- String template : STR. = string template processor - lets us write readable and easy strings with in embedded expression.
Expression can be any valid expression allowed in Java, like using operateor, calling methods, ternary opeartions etc.
- Sequenced collections - sits on top of the implementation that was written before the interfaces were introduced in Java 21.
interfaces like : SequencedCollection, SequencedSet and SequencedMap. These were introduced to make semantics clearer by providing
 the directional order and methods for first/last. Making intent more clearer in the type system.
```
