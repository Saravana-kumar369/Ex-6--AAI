<H3>NAME: SARAVANA KUMAR M</H3>
<H3>REGISTER NO.: 212222230133</H3>
<H3>EX. NO.6</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>
<H3>Aim: to perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.
<H3>Program:</H3>

```
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet

# Download necessary NLTK resources
nltk.download('punkt')
nltk.download('wordnet')
nltk.download('omw-1.4')
# Ensure the specific English tagger is downloaded
nltk.download('averaged_perceptron_tagger_eng')
nltk.download('punkt_tab')

# Input sentence
sentence = input("Enter a sentence: ")

# Tokenize and POS tagging
words = word_tokenize(sentence)
pos_tags = nltk.pos_tag(words)

print("\nPart of Speech Tags:")
for word, tag in pos_tags:
    print(f"{word:<10} - {tag}")

# Synonym and antonym collection
synonyms = set()
antonyms = set()

for word in words:
    # Wrap the synset loop in a try-except block to handle words not found in WordNet
    try:
        for syn in wordnet.synsets(word):
            for lemma in syn.lemmas():
                synonyms.add(lemma.name())  # Use set to avoid duplicates
                for ant in lemma.antonyms():
                    antonyms.add(ant.name())
    except nltk.corpus.reader.wordnet.WordNetError:
        # Optionally print a message or log that the word wasn't found in WordNet
        pass


print("\nSynonyms:", synonyms)
print("Antonyms:", antonyms)

```

<H3>Output</H3>
![image](https://github.com/user-attachments/assets/8403445a-84e5-4069-9956-4883b0dbcdfc)



<H3>Result:</H3>
Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
