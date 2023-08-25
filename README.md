# Language_evolution_model_mathematica

A group project done as part of a modelling theory course at university in 2022. The aim of the model was to look at the evolution of european languages, in particular, to model how transmissible a European language is to a person that speaks a different European language as their mother tongue. We started with a more abstract approach to set up the full project. We came up with the following questions: given a group of people, each with their own unique language, which language would dominate? Which language would have the most influence? 

The base model used to answer these questions is called the language evolution game model, found in the "AbstractLanguageEvolGame_V3" file. It is meant to simulate different forms of communication betweens individuals. Each individual has their own unique language which is represented by a matrix whose values range in between 0 and 1. This is called the Word Meaning Matrix (WMM for short). The columns each have a meaning and the rows have a word, such that a cell in a matrix is a word associated with a meaning. All the individuals must have the same words and meanings as their rows and columns. The higher number the entry is, the closer the word (the row the entry is found in) is associated to the meaning (the column the entry is found in).

I.e. Given an individual with a 2x2 WMM, whose columns are (Blue, Cloud) and rows (Azul, Nube). If entry (2,1)=1 then "Nube" means "Blue" in this persons language.

The game is played using a speaker and a listener who each have their own unique WMM. The speaker selects a meaning at random from thier matrix and based on the probability distribution of the words associated with the chosen meaning, selects a word at random. Meaning entries with higher values have a higher chance of being picked, this was done to create a bit of chaos, as well as add the simulation of someone misspeaking. The listner hears the word and then in turn selects a meaning based of the probability distribution of the meanings associated with the spoken word. If both the speaker and listener select the same entry in their WMM, communication has been a success, else it has failed.

I.e. Given a 2x2 WMM, whose columns are (Blue, Cloud) and rows (Azul, Nube). If the Speaker wants to say Blue and says the word Azul, the listener hears the word Azul and chooses the word Cloud, the communication between the individuals has failed.

Given a success in communication the entry in both the speaker and the listeners WMM increases by a value lamda. This can be whatever value you want it to be, depending on how much value you want the interaction to have on each individuals WMM. In other words the larger lamda is, the less amount of times in the individuals must communicate to one another in order to obtain the same language.

The model contains the following important variables: Lamda (impact of communication), WordNum and MeanNum (amount of rows and columns which correlate to the size of the WMM), PlayerNum (the amount of individuals) and RefinementThreshold (as some games may go on for a while we introduced a limit on how "refined" a language is. A language is refined once the WMM has only a single entry in each column, larger than the RefinementTreshold. Once this has occured to every indiduals WMM the game ends)
