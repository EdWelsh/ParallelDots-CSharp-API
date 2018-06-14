# ParallelDots-CSharp-API
CSharp Wrapper for ParallelDots APIs
#### Supported Environment
> .NET Framework 4.6.1
#### Installation

> Open the console in Visual Studio using the Tools > NuGet Package Manager > Package Manager Console command.

```sh
PM> Install-Package ParallelDots -Version 2.0.8
```
#### Languages Supported
	- Portuguese ( pt )
	- Simplified Chinese ( zh )
	- Spanish ( es )
	- German ( de )
	- French ( fr )
	- Dutch ( nl )
	- Italian (it)
	- Japanese ( ja )
	- Russian ( ru )
	- Thai ( th )
	- Danish ( da )
	- Finish ( fi )
	- Arabic ( ar )
	- Greek ( el )
  
  
#### Set a reference path in Visual C#

> Open the Reference Manager in Visual Studio using the Project > Add Reference > Browse.

> Then select the .dll file from path given below:

> ROOT_PATH\packages\ParallelDots.2.0.2\lib\Paralleldots.dll

#### Import ParallelDots namespace
```sh
using ParallelDots
```
#### Initialize Instance of paralleldots Class
```sh
using Newtonsoft.Json.Linq;
paralleldots pd = new paralleldots(<api_key>);

//define category for the custom classifier endpoint
JObject category = JObject.Parse(@"{'world politics': ['diplomacy', 'UN', 'war'], 'india': ['congress', 'india', 'bjp'], 'finance': ['markets', 'economy', 'shares']}");
```
#### Example
```sh

String path_to_image = @"<path_to_image>";
String url_to_image = "<url_to_image>";
JArray text_list = JArray.Parse("[\"drugs are fun\", \"don\'t do drugs, stay in school\", \"lol you a fag son\", \"I have a throat infection\"]");
JArray text_list_multilang = JArray.Parse("[\"les drogues sont amusantes\", \"ne pas faire de la drogue reste à l'école\", \"lol vous un fils de fag\", \"J'ai une infection de la gorge\"]");
String lang_text = "C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition.";

Console.WriteLine("abuse");
String abuse = pd.abuse("you f**king a$$hole");
Console.WriteLine(abuse);
abuse
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "sentence_type": "Abusive", "confidence_score": 0.953125}

Console.WriteLine("abuse_batch");
String abuse_batch = pd.abuse_batch(text_list);
Console.WriteLine(abuse_batch);
abuse_batch
{"batch": [{"sentence_type": "Non Abusive", "code": 200, "confidence_score": 0.904297}, {"sentence_type": "Non Abusive", "code": 200, "confidence_score": 0.953125}, {"sentence_type": "Abusive", "code": 200, "confidence_score": 0.884766}, {"sentence_type": "Non Abusive", "code": 200, "confidence_score": 0.859375}]}

Console.WriteLine("custom_classifier");
String custom_classifier = pd.custom_classifier("Narendra Modi is the Prime Minister of India", category);
Console.WriteLine(custom_classifier);
custom_classifier
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "taxonomy": [{"tag": "india", "confidence_score": 0.758248}, {"tag": "world politics", "confidence_score": 0.610343}, {"tag": "finance", "confidence_score": 0.371018}]}

Console.WriteLine("emotion");
String emotion = pd.emotion("Did you hear the latest Porcupine Tree song ? It's rocking !");
Console.WriteLine(emotion);
emotion
{"emotion": {"emotion": "Happy", "probabilities": {"Sarcasm": 0.0, "Angry": 0.0, "Sad": 0.0, "Fear": 0.0, "Bored": 0.0, "Excited": 0.04793506860733032, "Happy": 0.1406149665514628}}, "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

Console.WriteLine("emotion_multilang");
String emotion_multilang = pd.emotion("Avez-vous entendu la dernière chanson de Porcupine Tree? Ça berce!", "fr");
Console.WriteLine(emotion_multilang);
emotion_multilang
{"emotion": {"emotion": "Happy", "probabilities": {"Sarcasm": 0.0, "Angry": 0.0, "Sad": 0.03206148371100426, "Fear": 0.0, "Bored": 0.0, "Excited": 0.03780654817819595, "Happy": 0.0580072949330012}}, "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

Console.WriteLine("emotion batch");
String emotion_batch = pd.emotion_batch(text_list);
Console.WriteLine(emotion_batch);
emotion batch
{"batch": [{"emotion": {"probabilities": {"Bored": 0.06818537695928778, "Happy": 0.1269828871815771, "Fear": 0.344180628127824, "Sad": 0.025132654797074747, "Excited": 0.2082173830066366, "Sarcasm": 0.14361357966835644, "Angry": 0.08368749025924326}, "emotion": "Fear"}, "code": 200}, {"emotion": {"probabilities": {"Bored": 0.21483391837268373, "Happy": 0.11277100320338784, "Fear": 0.13348989058422842, "Sad": 0.05735552847026735, "Excited": 0.10118401124107868, "Sarcasm": 0.09578231410218406, "Angry": 0.28458333402617014}, "emotion": "Angry"}, "code": 200}, {"emotion": {"probabilities": {"Bored": 0.2922536573298578, "Happy": 0.07598588202024392, "Fear": 0.18020579627989994, "Sad": 0.05410169293913279, "Excited": 0.16457090063285224, "Sarcasm": 0.11124312097614852, "Angry": 0.1216389498218648}, "emotion": "Bored"}, "code": 200}, {"emotion": {"probabilities": {"Bored": 0.005730775686542725, "Happy": 0.005119673993076841, "Fear": 0.09443579921654321, "Sad": 0.3672790882763135, "Excited": 0.004337021311595699, "Sarcasm": 0.05327575096045899, "Angry": 0.46982189055546925}, "emotion": "Angry"}, "code": 200}]}

Console.WriteLine("emotion_multilang batch");
String emotion_multilang_batch = pd.emotion_batch(text_list_multilang, "fr");
Console.WriteLine(emotion_multilang_batch);
emotion_multilang batch
{"batch": [{"emotion": {"probabilities": {"Bored": 0.06818537695928778, "Happy": 0.1269828871815771, "Fear": 0.344180628127824, "Sad": 0.025132654797074747, "Excited": 0.2082173830066366, "Sarcasm": 0.14361357966835644, "Angry": 0.08368749025924326}, "emotion": "Fear"}, "code": 200}, {"emotion": {"probabilities": {"Bored": 0.08562579533950584, "Happy": 0.048649541948481326, "Fear": 0.09433366519047207, "Sad": 0.05560273629943171, "Excited": 0.04239430417791154, "Sarcasm": 0.07606870827400262, "Angry": 0.5973252487701952}, "emotion": "Angry"}, "code": 200}, {"emotion": {"probabilities": {"Bored": 0.22664523612567564, "Happy": 0.0987838892687481, "Fear": 0.16393978751891622, "Sad": 0.04597934708090136, "Excited": 0.20433981731805748, "Sarcasm": 0.13830145223523543, "Angry": 0.1220104704524655}, "emotion": "Bored"}, "code": 200}, {"emotion": {"probabilities": {"Bored": 0.005730775686542725, "Happy": 0.005119673993076841, "Fear": 0.09443579921654321, "Sad": 0.3672790882763135, "Excited": 0.004337021311595699, "Sarcasm": 0.05327575096045899, "Angry": 0.46982189055546925}, "emotion": "Angry"}, "code": 200}]}

Console.WriteLine("facial_emotion");
String facial_emotion = pd.facial_emotion(path_to_image);
Console.WriteLine(facial_emotion);
facial_emotion
{"code": 200, "facial_emotion": [{"tag": "Neutral", "score": 0.6072409749031067}, {"tag": "Angry", "score": 0.10396357625722885}, {"tag": "Sad", "score": 0.08047984540462494}, {"tag": "Surprise", "score": 0.05207890272140503}, {"tag": "Happy", "score": 0.05207890272140503}, {"tag": "Fear", "score": 0.05207890272140503}, {"tag": "Disgust", "score": 0.05207890272140503}]}

Console.WriteLine("facial_emotion_url");
String facial_emotion_url = pd.facial_emotion_url(url_to_image);
Console.WriteLine(facial_emotion_url);
facial_emotion_url
{"code": 200, "facial_emotion": [{"tag": "Neutral", "score": 0.45063450932502747}, {"tag": "Happy", "score": 0.1430361568927765}, {"tag": "Surprise", "score": 0.08126586675643921}, {"tag": "Sad", "score": 0.08126586675643921}, {"tag": "Fear", "score": 0.08126586675643921}, {"tag": "Disgust", "score": 0.08126586675643921}, {"tag": "Angry", "score": 0.08126586675643921}]}

Console.WriteLine("intent");
String intent = pd.intent("Finance ministry calls banks to discuss new facility to drain cash");
Console.WriteLine(intent);
intent
{"probabilities": {"marketing": 0.059, "spam/junk": 0.039, "news": 0.773, "feedback/opinion": 0.097, "query": 0.032}, "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "intent": "news"}

Console.WriteLine("intent batch");
String intent_batch = pd.intent_batch(text_list);
Console.WriteLine(intent_batch);
intent batch
{"batch": [{"code": 200, "probabilities": {"marketing": 0.116, "feedback/opinion": 0.141, "news": 0.08, "query": 0.002, "spam/junk": 0.66}, "intent": "spam/junk"}, {"code": 200, "probabilities": {"marketing": 0.106, "feedback/opinion": 0.393, "news": 0.051, "query": 0.027, "spam/junk": 0.423}, "intent": "spam/junk"}, {"code": 200, "probabilities": {"marketing": 0.001, "feedback/opinion": 0.333, "news": 0.001, "query": 0.001, "spam/junk": 0.664}, "intent": "spam/junk"}, {"code": 200, "probabilities": {"marketing": 0.0, "feedback/opinion": 0.469, "news": 0.004, "query": 0.404, "spam/junk": 0.124}, "intent": "feedback/opinion"}]}

Console.WriteLine("keywords");
String keywords = pd.keywords("Prime Minister Narendra Modi tweeted a link to the speech Human Resource Development Minister Smriti Irani made in the Lok Sabha during the debate on the ongoing JNU row and the suicide of Dalit scholar Rohith Vemula at the Hyderabad Central University.");
Console.WriteLine(keywords);
keywords
{"keywords": [{"keyword": "Prime Minister Narendra Modi", "confidence_score": 0.857594}, {"keyword": "link", "confidence_score": 0.913924}, {"keyword": "speech Human Resource", "confidence_score": 0.70655}, {"keyword": "Smriti", "confidence_score": 0.860351}, {"keyword": "Lok", "confidence_score": 0.945534}], "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

Console.WriteLine("keywords batch");
String keywords_batch = pd.keywords_batch(text_list);
Console.WriteLine(keywords_batch);
keywords batch
{"batch": [{"code": 200, "keywords": [{"confidence_score": 0.560126, "keyword": "fun"}]}, {"code": 200, "keywords": [{"confidence_score": 0.89078, "keyword": "drugs"}, {"confidence_score": 0.867192, "keyword": "school"}]}, {"code": 200, "keywords": [{"confidence_score": 0.731249, "keyword": "son"}]}, {"code": 200, "keywords": [{"confidence_score": 0.87782, "keyword": "throat infection"}]}]}

Console.WriteLine("language_detection");
String language_detection = pd.language_detection(lang_text);
Console.WriteLine(language_detection);
language_detection
{"prob": 0.9999592304229736, "code": 200, "output": "French"}

Console.WriteLine("language_detection batch");
String language_detection_batch = pd.language_detection_batch(text_list_multilang);
Console.WriteLine(language_detection_batch);
language_detection batch
{"batch": [{"prob": 0.9990742802619934, "code": 200, "output": "French"}, {"prob": 0.9999998807907104, "code": 200, "output": "French"}, {"prob": 0.996209442615509, "code": 200, "output": "French"}, {"prob": 0.9985631108283997, "code": 200, "output": "French"}]}

Console.WriteLine("multilang_keywords");
String multilang_keywords = pd.multilang_keywords("La ville de Paris est très belle", "fr");
Console.WriteLine(multilang_keywords);
multilang_keywords
{"keywords": ["paris", "ville", "belle", "tr\u00e8s"], "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

Console.WriteLine("ner");
String ner = pd.ner("Narendra Modi is the prime minister of India");
Console.WriteLine(ner);
ner
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "entities": [{"category": "name", "name": "Narendra Modi", "confidence_score": 0.951439}, {"category": "place", "name": "India", "confidence_score": 0.9263}]}
Console.WriteLine("ner batch");
String ner_batch = pd.ner_batch(text_list);
Console.WriteLine(ner_batch);
ner batch
{"batch": [{"entities": "The statement belongs to none of the categories.", "code": 200}, {"entities": [{"category": "name", "name": "don", "confidence_score": 0.671695}], "code": 200}, {"entities": "The statement belongs to none of the categories.", "code": 200}, {"entities": "The statement belongs to none of the categories.", "code": 200}]}

Console.WriteLine("nsfw");
String nsfw = pd.nsfw(path_to_image);
Console.WriteLine(nsfw);
nsfw
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output": "not safe to open at work", "prob": 0.7874962091445923}

Console.WriteLine("nsfw_url");
String nsfw_url = pd.nsfw_url(url_to_image);
Console.WriteLine(nsfw_url);
nsfw_url
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output": "safe to open at work", "prob": 0.9996483325958252}

Console.WriteLine("object_recognizer");
String object_recognizer = pd.object_recognizer(path_to_image);
Console.WriteLine(object_recognizer);
object_recognizer
{"output": [{"score": 0.21129773557186127, "tag": "Art"}, {"score": 0.180560901761055, "tag": "Person"}, {"score": 0.17255575954914093, "tag": "Sitting"}, {"score": 0.14926795661449432, "tag": "Statue"}, {"score": 0.1323658525943756, "tag": "Poster"}, {"score": 0.11433436721563339, "tag": "Sculpture"}, {"score": 0.1113261878490448, "tag": "Clothing"}, {"score": 0.08422151207923889, "tag": "Album cover"}, {"score": 0.08128573000431061, "tag": "Screenshot"}, {"score": 0.08076596260070801, "tag": "Illustration"}], "code": 200}

Console.WriteLine("object_recognizer_url");
String object_recognizer_url = pd.object_recognizer_url(url_to_image);
Console.WriteLine(object_recognizer_url);
object_recognizer_url
{"output": [{"score": 0.5784599781036377, "tag": "Screenshot"}, {"score": 0.2543911039829254, "tag": "Person"}, {"score": 0.20797836780548096, "tag": "Presentation"}, {"score": 0.14402228593826294, "tag": "Speech"}, {"score": 0.08889435976743698, "tag": "Man"}, {"score": 0.08697150647640228, "tag": "Brand"}, {"score": 0.06565890461206436, "tag": "Clothing"}, {"score": 0.06072978302836418, "tag": "Poster"}, {"score": 0.05715743452310562, "tag": "Face"}, {"score": 0.034983083605766296, "tag": "Advertising"}], "code": 200}

Console.WriteLine("phrase_extractor");
String phrase_extractor = pd.phrase_extractor("The girls giggling and playing in the park never seemed to tire");
Console.WriteLine(phrase_extractor);
phrase_extractor
{"keywords": [{"relevance_score": 1, "keyword": "tire"}], "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

Console.WriteLine("phrase_extractor batch");
String phrase_extractor_batch = pd.phrase_extractor_batch(text_list);
Console.WriteLine(phrase_extractor_batch);
phrase_extractor batch
{"batch": [{"code": 200, "keywords": []}, {"code": 200, "keywords": [{"keyword": "school", "relevance_score": 1}]}, {"code": 200, "keywords": [{"keyword": "fag son", "relevance_score": 2}]}, {"code": 200, "keywords": [{"keyword": "throat infection", "relevance_score": 2}]}]}

Console.WriteLine("popularity");
String popularity = pd.popularity(path_to_image);
Console.WriteLine(popularity);
popularity
{"Popular": "63.4013056755", "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "Not Popular": "36.5986973047"}

Console.WriteLine("popularity_url");
String popularity_url = pd.popularity_url(url_to_image);
Console.WriteLine(popularity_url);
popularity_url
{"Popular": "68.3887064457", "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "Not Popular": "31.6112935543"}

Console.WriteLine("sentiment");
String sentiment = pd.sentiment("Come on, lets play together");
Console.WriteLine(sentiment);
sentiment
{"probabilities": {"positive": 0.096, "neutral": 0.891, "negative": 0.013}, "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "sentiment": "neutral"}

Console.WriteLine("sentiment_multilang");
String sentiment_multilang = pd.sentiment("Allez, jouons ensemble", "fr");
Console.WriteLine(sentiment_multilang);
sentiment_multilang
{"probabilities": {"positive": 0.223, "neutral": 0.764, "negative": 0.013}, "usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "sentiment": "neutral"}

Console.WriteLine("sentiment batch");
String sentiment_batch = pd.sentiment_batch(text_list);
Console.WriteLine(sentiment_batch);
sentiment batch
{"batch": [{"sentiment": "positive", "code": 200, "probabilities": {"negative": 0.046, "positive": 0.69, "neutral": 0.265}}, {"sentiment": "neutral", "code": 200, "probabilities": {"negative": 0.361, "positive": 0.061, "neutral": 0.578}}, {"sentiment": "positive", "code": 200, "probabilities": {"negative": 0.275, "positive": 0.527, "neutral": 0.198}}, {"sentiment": "negative", "code": 200, "probabilities": {"negative": 0.908, "positive": 0.077, "neutral": 0.015}}]}

Console.WriteLine("sentiment_multilang batch");
String sentiment_multilang_batch = pd.sentiment_batch(text_list, "fr");
Console.WriteLine(sentiment_multilang_batch);
sentiment_multilang batch
{"batch": [{"sentiment": "positive", "code": 200, "probabilities": {"negative": 0.046, "positive": 0.69, "neutral": 0.265}}, {"sentiment": "neutral", "code": 200, "probabilities": {"negative": 0.429, "positive": 0.053, "neutral": 0.518}}, {"sentiment": "positive", "code": 200, "probabilities": {"negative": 0.378, "positive": 0.395, "neutral": 0.226}}, {"sentiment": "negative", "code": 200, "probabilities": {"negative": 0.908, "positive": 0.077, "neutral": 0.015}}]}

Console.WriteLine("similarity");
String similarity = pd.similarity("Sachin is the greatest batsman", "Tendulkar is the finest cricketer");
Console.WriteLine(similarity);
similarity
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "actual_score": 0.842932, "normalized_score": 4.931469}

Console.WriteLine("taxonomy");
String taxonomy = pd.taxonomy("Narendra Modi is the prime minister of India");
Console.WriteLine(taxonomy);
taxonomy
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "taxonomy": [{"tag": "News and Politics/International News", "confidence_score": 0.729859}, {"tag": "Business and Finance/Economy", "confidence_score": 0.738674}, {"tag": "Sports/Cricket", "confidence_score": 0.875686}]}

Console.WriteLine("taxonomy batch");
String taxonomy_batch = pd.taxonomy_batch(text_list);
Console.WriteLine(taxonomy_batch);
taxonomy batch
{"batch": [{"taxonomy": [{"confidence_score": 0.996437, "tag": "health and fitness/drugs"}, {"confidence_score": 0.967404, "tag": "family and parenting/babies and toddlers"}, {"confidence_score": 0.6848993897438049, "tag": "automotive and vehicles/motor shows"}], "code": 200}, {"taxonomy": [{"confidence_score": 0.977439, "tag": "health and fitness/dental care"}, {"confidence_score": 0.961832, "tag": "family and parenting/babies and toddlers"}, {"confidence_score": 0.970684, "tag": "education/school"}], "code": 200}, {"taxonomy": [{"confidence_score": 0.9779467582702637, "tag": "family and parenting/parenting teens"}, {"confidence_score": 0.972425, "tag": "health and fitness/therapy"}, {"confidence_score": 0.9049649834632874, "tag": "pets/cats"}], "code": 200}, {"taxonomy": [{"confidence_score": 0.985712, "tag": "health and fitness/disease"}, {"confidence_score": 0.974752, "tag": "family and parenting/adoption"}, {"confidence_score": 0.97041, "tag": "pets/cats"}], "code": 200}]}

Console.WriteLine("text_parser");
String text_parser = pd.text_parser("Thrilling contest between Manchester City and Manchester United ends in a draw.");
Console.WriteLine(text_parser);
text_parser
{"usage": "By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output": [{"text": "Thrilling", "Dependency": "compound", "Tags": "noun"}, {"text": "contest", "Dependency": "nominal subject", "Tags": "noun"}, {"text": "between", "Dependency": "prepositional modifier", "Tags": "preposition or conjunction"}, {"text": "Manchester", "Dependency": "compound", "Tags": "noun"}, {"text": "City", "Dependency": "object of a preposition", "Tags": "noun"}, {"text": "and", "Dependency": "coordinating conjunction", "Tags": "conjuction"}, {"text": "Manchester", "Dependency": "compound", "Tags": "noun"}, {"text": "United", "Dependency": "conjunct", "Tags": "noun"}, {"text": "ends", "Dependency": "root", "Tags": "verb"}, {"text": "in", "Dependency": "prepositional modifier", "Tags": "preposition or conjunction"}, {"text": "a", "Dependency": "determiner", "Tags": "determiner"}, {"text": "draw", "Dependency": "object of a preposition", "Tags": "noun"}]}

Console.WriteLine("usage");
String usage = pd.usage();
Console.WriteLine(usage);
usage
{"monthly_billable_hits_breakdown": {"emotion": 7592, "facial_emotion": 7, "sentiment": 7763, "similarity": 7543, "language_detection": 30, "taxonomy": 7570, "popularity": 773, "text_parser": 7540, "custom_classifier": 7547, "abuse": 7587, "intent": 7576, "multilang_keywords": 15079, "keywords": 7599, "nsfw": 772, "object_recognizer": 6, "ner": 22679, "phrase_extractor": 7600}, "daily_billable_hits_breakdown": {"emotion": 377, "facial_emotion": 6, "sentiment": 387, "similarity": 346, "language_detection": 22, "ner": 1055, "popularity": 6, "text_parser": 345, "custom_classifier": 345, "abuse": 378, "intent": 366, "taxonomy": 366, "keywords": 366, "nsfw": 6, "object_recognizer": 6, "multilang_keywords": 687, "phrase_extractor": 365}, "daily_billable_hits": 5429, "monthly_billable_hits": 115263}


```
