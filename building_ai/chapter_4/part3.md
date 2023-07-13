# III. Deep learning

Until now, we've intentionally discussed relatively simple models in order to make sure we can understand them and avoid becoming some sort of "data alchemists" who just keep stirring the pile until something useful arises.

Now that we're familiar with the basics, we can fast forward to the current state-of-the-art techniques, even if we'll have to skim over most of the technical details. The word revolutionize tends to be used way too much and it tends to correlate with bulls**t, but we think it's fair to say that data science has been revolutionized by easy-to-use deep learning tools and platforms. Platforms such as Google's Tensorflow, Facebook's PyTorch, and fast.ai enable pretty much anyone who has the tenacity to spend a few months learning the tricks of the trade to build amazing AI solutions for practical problems.

Progress in the last decade has been a-m-a-z-i-n-g (to use the technical term) especially in the fields of natural language processing and image processing. In natural language processing, problems such as machine translation, text summarization, and question answering were really lagging behind from areas where the data were numbers or symbols. The same could be said about image processing, where progress in image recognition and various image enhancement tasks was painfully slow until people started to experiment with deep learning techniques.

There are a few additional innovations that have enabled quantum leaps in specific fields. We'll introduce a few of them here.

## Convolutional neural networks (CNNs)

The scary sounding name hides a pretty simple overall idea. As we discussed above, one of the drawbacks of large neural networks is the fact that a large number of parameters requires both a lot of data and a lot of computation. There really aren't that many ways to cope with small networks when dealing with images because images contain a lot of pixels and the devil is often in the details. The first layer of the network that is directly processing the pixel-level data has to have at least as many parameters as there are pixels. Otherwise some of the pixels aren't connected to anything and they will be ignored.

The key insight in CNNs is the realization that even if there are millions of parameters related to the pixels of the input image, there doesn't necessarily have to be millions of different parameters. A CNN is composed of a collection or "bank" of so- called filters that are rectangular image patches much smaller than the original image. These filters are matched to different places on the image in a process that corresponds to the mathematical operation of convolution, hence the name CNN.

In terms of the neural network architecture, each filter corresponds to a set of parameters that are used to multiply pixel values inside the rectangular patch. The same set of parameters is shared by different neurons that process inputs within different patches. The network can contain multiple convolutional layers: in the first layer, the patches contain pixels in the original image, and in the further layers, the patches contain outputs from the previous layer which is structured in a rectangular form just like the input image.

### UNICEF school mapping 

How many schools are there in your country and where are they are located? In a lot of places around the world, the answer is “not sure”. Schools may be in remote locations and unconnected to the internet or phone lines, meaning expensive ground mapping is needed to find them all.

Having an accurate and comprehensive map of schools is a key tool for measuring and improving the quality of learning. Such a map can also be combined with digital connectivity initiatives to improve access to information, as well as to help governments and international organizations to better prepare and respond to shocks such as disease outbreaks or natural disasters.

In order to help countries create accurate school maps, UNICEFand Development Seed decided to use AI methods. Using high-resolution satellite images, a neural network was trained to identify features that can identify school buildings.

**The problem**
In many countries around the world, records of school locations are inaccurate, incomplete, or non-existent.

**The solution**
Using a combination of deep machine learning techniques and trained human mappers, UNICEF and Development Seed are combining high-resolution imagery and inexpensive cloud computing to create a comprehensive map of schools on a country-wide scale.

**AI methods used**
Training data from an existing school map of Columbia was used to tune the algorithm for a school classifier based on a convolutional neural network (CNN). The CNN was created by modifying existing tools based on Xception and MobileNetV2 so that they could use satellite imagery.

They selected the best-performing model from nearly 200 training iterations and applied it across Colombia and the Eastern Caribbean islands to detect potentially unmapped schools. Running the model over such a large area of high-resolution imagery is a huge task – over 52 million images had to be processed. Development Seed created an open source tool, chip-n-scale-queue-arranger, to manage the high-volume satellite imagery inference tasks.

**The process**

+ Create a high-quality map of known schools in a country
+ Generate a training dataset
+ Create and tune a school classifier
+ Run the model in another country to identify candidate unmapped schools
+ Validate these predictions with people on the ground

  

## Recurrent neural networks (RNNs) and transformers

The word transformer also refers to a particular neural network architecture.

Recurrent neural networks (RNNs) are a class of architectures where the data is not processed in a linear progression from the input through a number of hidden layers towards the output. Instead, some of the layers are connected backwards to the previous layers, forming feedback loops where some neurons process the data multiple times before the output is produced. RNNs are more complex and generally even harder to train from data than simple feedforward networks like the ones we discussed in earlier sections.

The greatest advantage of RNNs is the fact that they enable mechanisms where the network "remembers" things that have occurred in the data even beyond the current input. When modeling text, this enables models that remember what was said earlier. For example, if the text starts with "Soile has a new puppy. She showed me a picture of it today," the model can link the word "She" with "Soile" and the word "it" with "new puppy" even if the whole piece of text isn't processed as one input sequence. This is useful for machine translation and text generation. If the text would continue "It looks..." a likely continuation would be "adorable" or "SOOOOOO cute!!!!!" (depending on whether the network is trained on BBC news reports or Reaktor Slack content) while the same continuation would be quite unlikely if instead of the word "puppy" we would have had the word "chainsaw" or "Harley Davidson".

The transformer architecture is a technique for avoiding the use of a recurrent neural network and still having the ability to identify long-range dependencies between words. The technique is based on so-called attention mechanisms that identify the most relevant words to be used in predicting the likely continuation of a piece of text. The same architecture can also be used for machine translation. Transformer networks are currently the most popular approach for text modeling because they require less computation than RNNs. They are currently the state-of-the-art solution in most natural language processing tasks.

The most famous instance of a transformer network is the GPT-2 (Generative Pretrained Transformer 2) network created by Open.AI researchers in 2019. It created quite a storm in a teacup amongst the AI crowd when the developers announced that at the first stage, they would only release a miniature version with "only" 345 million parameters instead of the full-blown model with a whopping 1.5 billion parameters. Their explanation was that the release of the full-blown model would be too risky and that society would be "unprepared" for large language models. The possibility to use advanced text generation methods for the mass production of malicious content gives reason for concern. Quoting the Open.AI team:

"We can also imagine the application of these models for malicious purposes, including the following (or other applications we can’t yet anticipate):

+ Generate misleading news articles
+ Impersonate others online
+ Automate the production of abusive or faked content to post on social media
+ Automate the production of spam/phishing content

These findings, combined with earlier results on synthetic imagery, audio, and video, imply that technologies are reducing the cost of generating fake content and waging disinformation campaigns. The public at large will need to become more skeptical of text they find online, just as the "deep fakes" phenomenon calls for more skepticism about images."

source: [better-language-models](https://openai.com/blog/better-language-models/)

The Open.AI team did eventually release the full 1.5 billion parameter model to the public, and since then developed an even larger model, the GPT-3 with 175 billion parameters. Whether the dangers the Open.AI team envisioned will turn out to be true remains to be seen.

---
You've reached the end of Chapter 4!
---

## After completing this chapter, you should be able to:
- Explain and use sigmoid functions and logistic regression
- Explain the advantages of neural networks and how to build a simple neural network
- Discuss what deep learning is and what are some current “hot topics” in the field
