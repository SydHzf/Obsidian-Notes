*Over stemming* -> two different context words have same stem form.
*Under stemming* -> two same context words have different stem form.
### **Benefits of Stemming:**

- **Computational Efficiency:** Stemming is generally faster and computationally less expensive than lemmatization.
- **Simplicity:** Stemming algorithms are simpler to implement and maintain.

### **Benefits of Lemmatization:**

- **Precision:** Lemmatization provides more accurate results by considering the context of words in a sentence.
- **Context Awareness:** It helps in maintaining the semantic meaning of words, which is crucial in applications like natural language processing.

### **TF-IDF (Term Frequency-Inverse Document Frequency):**

**Definition:**
TF-IDF is a statistical measure used in natural language processing and information retrieval to evaluate the importance of a word in a document relative to a collection of documents. It combines two components: Term Frequency (TF) and Inverse Document Frequency (IDF).

**Term Frequency (TF):**
TF measures how frequently a term occurs in a document. It is calculated as the ratio of the number of times a term appears in a document to the total number of terms in the document.
TF(t,d)=Total number of terms in document d/Number of occurrences of term t in document d​

**Inverse Document Frequency (IDF):**
IDF measures the rarity of a term across a collection of documents. It is calculated as the logarithm of the ratio of the total number of documents to the number of documents containing the term.

\[ \text{IDF}(t, D) = \log\left(\frac{\text{Total number of documents in the collection } D}{\text{Number of documents containing term } t}\right) \]

**TF-IDF Calculation:**
The TF-IDF score for a term \(t\) in a document \(d\) is obtained by multiplying the term frequency (\(\text{TF}(t, d)\)) and the inverse document frequency (\(\text{IDF}(t, D)\)).

\[ \text{TF-IDF}(t, d, D) = \text{TF}(t, d) \times \text{IDF}(t, D) \]

**Example:**
Consider a collection of three documents:

1. Document 1: "Machine learning is fascinating."
2. Document 2: "Fascinating concepts of machine learning."
3. Document 3: "I enjoy learning about machine learning."

Let's calculate the TF-IDF scores for the term "machine" in each document.

1. **Document 1:**
   - TF("machine", Document 1) = 1/4
   - IDF("machine", Collection) = log(3/3) = 0
   - TF-IDF("machine", Document 1, Collection) = (1/4) * 0 = 0

2. **Document 2:**
   - TF("machine", Document 2) = 1/5
   - IDF("machine", Collection) = log(3/3) = 0
   - TF-IDF("machine", Document 2, Collection) = (1/5) * 0 = 0

3. **Document 3:**
   - TF("machine", Document 3) = 2/6
   - IDF("machine", Collection) = log(3/3) = 0
   - TF-IDF("machine", Document 3, Collection) = (2/6) * 0 = 0

In this example, the TF-IDF scores for the term "machine" are zero for all documents because the term appears in every document, making its IDF value zero. In practice, TF-IDF is more useful when considering terms that are not ubiquitous across all documents in the collection.