# Operators

Operators can be seen as tiny programs that can be chained together to build all sorts of things. There are a lot of them, and they come in various types. Most operators have inputs and outputs, expecting data to arrive on the left \(input\), and then present data on the right \(output\), ready to be retrieved.

Press `TAB`  or right-click and select **Add operator** to open the OP Create Dialog \(list of operators\). The operator types are seen in the top, hover over the label to see a description at the bottom of the window. Press `TAB` again to cycle between the different operators. The most commonly used operators are the TOP, CHOP, SOP and DAT.

{% tabs %}
{% tab title="TOP" %}
Texture operators are **purple**, the fastest and most powerful component in TD, and handle anything related to pixel data; composing image streams, blurring, detecting edges or handling external devices like depth cameras to point clouds.
{% endtab %}

{% tab title="CHOP" %}
Channel operators are **green** and are mostly made to do math and logic operations. This way you can program behaviour which can in turn be placed onto parameters of other operators to automatically control them.
{% endtab %}

{% tab title="SOP" %}
Surface operators are **blue** and relate to shapes in 3D space.
{% endtab %}

{% tab title="DAT" %}
Data operators are **violet-red** and can be used to handle data, text and scripting. DATs often go hand in hand with Python!
{% endtab %}
{% endtabs %}

![](../../../.gitbook/assets/image%20%2842%29.png)

![An example of typical operators of various types](../../../.gitbook/assets/image%20%2820%29.png)



