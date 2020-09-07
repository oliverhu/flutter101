# Flutter Notes

## Thoughts

I plan to write an app to record puppy behaviors, and I didn't find any compelling app on the App Store, so I decided to write one myself. The natural follow-up topic is to decide the technology choice. For server side, Django + Rest is good enough and that is the choice of mine for most web service server side development. Making a technology choice for client side development has always been a more challenging one:

- What language to use? Swift vs Objective-C for iOS, Kotlin vs Java for Android.
- What platform to support? Does it make sense to support Android? (Android annecdotally generates less revenue thatn iOS)
- Cross platform or develop for different platforms?

I have been a strong believer in native development for large corps, because they can afford large teams and going native always bring best performance *and* native is much more mature than any 3rd party frameworks. But I'm swaying for small teams, like my hackday projects with 2 - 3 friends. For my previous app, I need to tinker a lot on networking layer and UX is not very complex, so I chose to use Swift for UI and Objective-C & C for networking plugins. This time, it would be a fairly UI heavy app (meaning, less lower level OS integration), we decided to use Flutter.

## Flutter vs React Native vs Native vs HTML5
Some understanding after reading blog posts around Flutter. Also took a look at Airbnb's journey on hybriding RN & Native - [pretty bad experience](https://medium.com/airbnb-engineering/react-native-at-airbnb-the-technology-dafd0b43838):

- You intent to share code to develop using 1 platform (RN), but it turned out to be everybody has to learn developing under 3 platforms: iOS, Android and Web. Because RN uses native component to render and if you want to build a highly customized experience, which is common for a larger corp, the guy who is building the feature has to implement the experience for all platforms.
- RN is no where close to the maturity of native. It is not a problem for small teams, they can work around bugs by working around the features; but for large companies, developers have to fight againt the bug in RN instead of fighting with the execs..
- Hiring is challenging, attribution is big, hard to organize the teams.


### Native
Native has the best performance, best of class support from OS provider. Quick to develop and debug. The only drawback, and also the largest drawback is the **development cost**. iOS and Android have completely different stack, ranging from language, design pattern, IDE, development environment (you can't develop iOS in non macos environment at all). You either have to learn developing in both platforms or building a team with expertise in both platforms. Another problem of developing under different teams is: it is also hard to make the UX consistent cross the two platforms.

### HTML5
Both iOS and Android have very good WebView support, like WKWebView (iOS) or WebView (Android). Native also exposes endpoints for HTML5 to interact to gain access to local, so you can theoretically access most other components in native. However, the biggest drawback of HTML5 is performance. It is very heavy to load, parse and render a HTML5 page.

```
JS
--
WebView
--
OS Canvas
```

### RN
RN provides a common JS interface to develop and uses native component/engine to render. But it has the issues mentioned above in AirBnb's case.

```
JS
--
JS Bridge
--
Native component
OS Canvas

```

### Flutter
Flutters is like the next gen of RN. It basically abstracts out the whole layer (UIKit), and provide a cross platform UI framework including rendering logic. Note, flutter doesn't abstract the OS (iOS vs Android), but the UI layer, which is the component frontend developer spends most time dealing with. 

```
Dart
--
Cross platoform render engine
--
OS Canvas
```


