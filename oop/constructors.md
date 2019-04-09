# Constructors
## Overview
## Additional Materials
## Questions
1. :star: Where should an instance variable be initialized?
## Answers
1. In a constructor. It is legal to initialize them where they are declared, but it's better style to do it in a constructor. If you initialize one *both* where it is declared *and* in a constructor, anyone reading your code will have to both notice this and look up which one takes precedence. It is better to be consistent. Since complicated multi-line initializations (e.g., arrays that have to be filled in with loops) can only happen in the constructor, it's best to put all initializations there.
