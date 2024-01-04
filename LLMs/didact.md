# DidAct: Large sequence models for software

## overview
 - looking at code, git history, github work, to collect data on how devs look at/work on/reflect on code
 - Multi-task code training
 - Tasks
    - Debug and repair
        - Build repair
        - Build error prediction
        - TFix
    - Code review
        - Comment prediction
        - tip prediction
        - comment repair
        - presubmit cleanup
        - readability renames
        - code review auto-complete
    - Code Editing
        - Edit prediction
        - Span denoising
        - Variable renaming
        - history-augumented code completion
        - prompting and chaining
 - Google internal repo? high quality code? useful
 - the internal repo comment history/reviews are invaluable data, other systems have no mass github scrapes for non-code work
 - Input is code and task, returns action
 - Knowing the thought process of the prev. dev who worked on the code helps the model figure out a better course of action
 - worked like a developer, going step by step, building out a code skeleton, then adding functionality piece by piece

## future work
 - fully autonomus code gen, working code, code-interpreter style, feedback loop
 - adding more github history into the training data, moving past google-ish code
 - Extra tasks
    - full code explanation - getting the model to look through code files/repos, and trace all the functions and their relationships to answer queries 
    - Unit tests - reasoning/defining then implementing unit tests, validating them against the code
    - old code removal - runs the program and removes unused/dead code? could be possible to leave comments near incomplete code to stop that
    - optimizing code? - recommend time/space complexity changes
    - language to language - somewhat farfetched, but moving from (ex. py to js), and not just the basics of the language, but also the other parts, like how the api changes per language, optimize each language?
    - adding 3rd party apis/libs to code making/edits
    - security warnings/secure code edits
    - using repos with context to prev issues/bugs