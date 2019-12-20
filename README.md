# Change locale sample

It is just adopted from our [customization-change-locale](https://github.com/microsoft/BotFramework-WebChat/tree/master/samples/22.customization-change-locale) sample application.

## Select Voice

```
        // createCognitiveServicesSpeechServicesPonyfillFactory const parameter is pulled from WebChat
        const { createDirectLine, createStore, ReactWebChat, createCognitiveServicesSpeechServicesPonyfillFactory } = window.WebChat;

        const selectVoice = useMemo(() => (voices, activity) => {
            // if want to study voices/ activity values, uncomment the below
            //console.log(`voices - before if - ${JSON.stringify(voices)}`);
            //console.log(`activity - before if - ${JSON.stringify(activity)}`);
            /*
            // activity.locale can contain value only if bot service Activity have set in response
            // out here, logic could be read locale from client on the bot service level/ respond with Activity object via same locale
            // voice value can be set as per - https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support#standard-voices
            **/
            if (activity.locale === 'zh-HK') {
                console.log(`in if`);
                return voices.find(({ name }) => /TracyRUS/iu.test(name));
            } else {
                // by-default it assumes the voice locale is 'en-US'
                console.log(`in else`);
                return voices.find(({ name }) => /JessaRUS/iu.test(name));
            }
        });

        // Render Web Chat with the specific locale. 
        return <ReactWebChat directLine={directLine}
                      locale={locale}
                      selectVoice={selectVoice}
                      store={store}
                      webSpeechPonyfillFactory={webSpeechPonyfillFactory} />;
```

