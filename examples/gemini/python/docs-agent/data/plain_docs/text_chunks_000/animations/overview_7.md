The Simulation abstract class maps a
relative time value (an elapsed time) to a
double value, and has a notion of completion.
In principle simulations are stateless but in practice
some simulations (for example,
BouncingScrollSimulation and
ClampingScrollSimulation)
change state irreversibly when queried.
There are various concrete implementations
of the Simulation class for different effects.
