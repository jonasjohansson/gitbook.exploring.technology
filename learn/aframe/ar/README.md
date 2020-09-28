# Augmented Reality

Computer vision algorithms is what drives AR, and as cameras and the computing power of mobile devices, so does also the portable AR capabilities. It's a [fascinating subject](https://www.sciencedirect.com/topics/computer-science/augmented-reality) that will continue to become  dominant in our everyday life, probably sooner than we think. AR in the browser is developing fast, thanks to efforts by the [AR.js](https://ar-js-org.github.io/AR.js-Docs/) team led by [Nicolò Carpignioli](https://twitter.com/nicolocarp). There are currently three tracking methods available:

{% page-ref page="marker/" %}

{% page-ref page="location.md" %}

{% page-ref page="image.md" %}

{% hint style="danger" %}
Because AR attaches the world to a marker `<a-sky>` won't work!
{% endhint %}

{% hint style="warning" %}
The benefit of using \(open-source\) WebAR is iteration speed and accessibility, while the downside is \(sadly\) quality. It's not as robust or smooth as it's native counterparts. There are however paid options such as [8th Wall](https://www.8thwall.com/) that provide solid experiences.
{% endhint %}

## Improving performance

While not heavily tested, it might be possible to gain an increase in performance by adding `renderer="logarithmicDepthBuffer: true;"` to  `<a-scene>`.

