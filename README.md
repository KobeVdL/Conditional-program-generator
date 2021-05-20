# ProgramPreconditionGenerator
Haskell generator for programs that always fulfill the given preconditon.
## How to get started?
The generator is fully written in Haskell so make sure you install Haskell first, this can be done on https://www.haskell.org/platform/.
Secondly you need to install ghci and stack, stack is needed to include randomness in the algorithm.
For testing you need to make sure you installed the latest ghci (package timeit).

## Information about the classes used
* **BasicProlog** - This class has the basic constructor to construct a Horn clause program, furthermore it also includes functions to bind variables to the given  term/predicate/rule. The classes supported are the following:
  * **Term** - The basic building blocks of our program, a term is a constant, an atom or a variable. Example: true = MkTerm "true" 0 [] 
               
               The first argument describes the name of the term, make sure not to use names that consist of "_"[Number] then the renaming algorithm won't work.
               The second argument describes the cardinality of the term, this is 0 for a constant and 1 or more for atoms.
               The third argument describes the inner terms inside this term, this is an empty list for constants, take for example not(true) this is created as
               follows:  MkTerm "not" 1 [MkTerm "true" 0[]].
               A variable is created as follows: Variable "name" . Its only argument is a name of the Variable
  * **Predicates** - These are very similar to terms but describes the relation between the arguments, predicates always form the outer layer of terms inside a rule. The key difference is that a Predicate can't be a Variable, an example of a predicate is isSuccOf(zero,succ(zero)). The arguments are the same as a term but instead the MkPredicate is used.
  * **Clause** A clause consist of a headPredicate and its body which is a list of predicates. The clauses work exactly the same as a prolog program and are constructed as follows. Rule [Put your Predicate here] [Put your list of Predicates here].
  * **Program** To end this we have als a Program which is just a list of rules and is created with a MkProgram.
* **BasicStep** This class is used as a basic case that a new programming language could simplify a program. This simplification step should be changed by your needs for a new programming language.
* **BottomUp** This class describes the bottom-up approuch for generating new programs that fulfill the given precondition.
* **Constructors** Some example Programs used for testing.
* **CounterExampleAlgorithms** Use the 3 generating algorithms to find a counterExample these are compared to each other.
* **NaiveGenerator** The algorithm that just random generates programs and don't look at given preconditions. If the generated program does not fulfill the precondition it just tries again.
* 
