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
```
21/1/26
- Clean code : clean code keeps software evolving
1. Naming - API of our thoughts - make the intent explicit with names : be specific
2. Clean Function : only one work for a func, be as less as possible: 20 lines, 2-3 arguments
3. Comment : when not able to express the intent in code, then will use comments apart from public API docs, license etc
4. Formatting and indentation : Tools to be used for this
5. Code smells : signals of bad design : long methods, large classes, duplicate code, feature envy, magic values.
6. Refactoring : refactor when behavior is protected : changing names, extracting methods, replacing magic values, moving code without changing bahavior.
7. Error handling : never catch which you can't handle, validate the boundarines, avoid pointless battles
8. Dependency management : High level policy must not depend on low level details : Control relationships not individuals
9. Test driven development : TDD: First right minimal correct code from failed tests, then refactor to improve design.
```
