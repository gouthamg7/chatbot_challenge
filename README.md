# chatbot_challenge

Pre-Requisites:
Anaconda and Docker to be installed for running the project

1. Install and run LASER on port 8050 by running the following commands:

    git clone https://github.com/facebookresearch/LASER
    cd LASER
    docker build --tag=laser docker
    docker run -p 8050:80 -it laser python app.py

2. Install ChatbotNER and run it on port 8081 by running the following commands:

    git clone https://github.com/hellohaptik/chatbot_ner.git
    cd chatbot_ner 
    cp config.example .env
    cp .env docker/.env
    cd docker
    docker-compose up --build -d

3. Language Detection API: Download Tatoeba dataset and Dakshina dataset for training of Language Detection Model from https://downloads.tatoeba.org/exports/sentences.csv, https://storage.googleapis.com/gresearch/dakshina/dakshina_dataset_v1.0.tar. Run the Language Detection API that starts on port 5000. This API is used in classifier for language detection of Hindi to English Transliterated utterances. This API works for Hindi and English language detection. Install tensorflow 2x, keras, scikit-learn, matplotlib(for creating confusion matrix) for running the file.
    Note: Refer to LanguageIdentification_4.ipynb for lanugage detection model that supports Hindi, Telugu, Tamil and English

4. Classifier API: Install Tensorflow 1x, tflearn, numpy for running Classifer.ipynb. Training data is included in file banking_intents.json. The API runs on port 7000.

Once all the 4 APIs mentioned are running, then the model can be tested by using the endpoint http://127.0.0.1:7000/predict?utterance=<utterance>

'intent' field in the response has the predicted intent. 'lang' field represents detected language. And, 'entities' field displays identified entities.