!pip uninstall spacy
!pip install spacy==2.2.4
!pip install https://github.com/explosion/spacy-models/releases/download/en_core_web_sm-2.2.0/en_core_web_sm-2.2.0.tar.gz

import spacy

# Import the Matcher
from spacy.matcher import Matcher

#Load a model and create the nlp object
nlp = spacy.load("en_core_web_sm")

# Initialize the matcher with the shared vocab
matcher = Matcher(nlp.vocab)

text = "After making the iOS update you won't notice a radical system-wide "
    "redesign: nothing like the aesthetic upheaval we got with iOS 7. Most of "
    "iOS 11s furniture remains the same as in iOS 10. But you will discover "
    "some tweaks once you delve a little deeper, about 60%."

pattern = [{"IS_DIGIT": True}]
matcher.add("numero", None, pattern)
doc = nlp(text)

# Call the matcher on the doc
matches = matcher(doc)

if not(matches):
  print("El texto debe contener al menos 1 número")
else:
  print("Numeros en el texto: ")
  for match_id, start, end in matches:
    # Get the matched span
    matched_span = doc[start:end]
    print(matched_span.text)
