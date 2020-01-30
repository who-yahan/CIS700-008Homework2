# CIS700-008Homework2

# Explanation for Part 2
Implement WordNet/Word Embeddings to Action Castle text game. 

I have added construct_sentence_vector, find_most_similar_command functions to Parser. When dealing with special_commands, which means commands connected with items, we can enlarge the range of decsription from users.

There are three parameters in find_most_similar_command function. One is user_command. This is set by the user input. Another is known_command. This is set by item.command(). If user enter something similar to the known_command, it will not be wrong. For example, "pick rose" and "pick up rose", the distance is 0.38, then we can get the same action result.

However, we need to pay attention to the similarity or the distance value for the two commands. For example, "pick rose" and "eat rose". the distance is 0.76, then we can't use them as the same. Instead, we should classify the latter as a wrong command. 

Another part I have changed is "look". Use self.vectors.similarity to classify the 
Synonyms. Then the command words for doing "look" function is enlarged. For example, "look" and "see" have the same action result.
  
# Discussion for Part 3
Integrate some other NLP technology into my game parser.

I have used AllenNLP dependency parser to mygame.Before we can just use one command at a time. For example. "look" and "examine an object" must be seperated by "," or they must be seperated input. However, if we use AllenNLP dependency parsing, the command in the same sentence can be seperated automatically.

I have added it to the part. When there are more than one "verb object" pair, the output of get_player_intent function will be "sequence". Then we can do setence segmentation as pair[0] + " " + pair[1] to get new command segments.

For example, we can use commad "look and examine the door"， which is same as "look, examine the door". 
