---
description: OpenGL Shading Language
---

# GLSL

This page is about pixel shaders, also know as fragment shaders.

{% hint style="success" %}
GLSL code runs in parallel on on the **GPU**.
{% endhint %}

The same code get's executed on each pixel.

In a one megapixel image \(1000x1000\), the code runs one million times for a single frame.

Now based on the pixel location, the UV coordinate, you calculate a single color of RGBA.

{% hint style="info" %}
UV coordinates are represented as floating point values between 0.0 and 1.0
{% endhint %}

**GLSL vs GLSL Multi TOPs**: They are the same, with the difference that the latter has support for more inputs than the first.

{% hint style="info" %}
_vec4_ is a value type with 4 floats, usually: red, green, blue and alpha.
{% endhint %}

## High Bit Color

It's convenient to work with high bit color for two main reasons.

* **Accuracy -** 16 bit has way more accuracy than 8 bit. 65 536 vs 256 steps.
* **Range** - 16 and 32 bit color can go beyond 0.0 and 1.0, negative values are supported, the values are not clamped.

## The Default Shader

```text
// Example Pixel Shader

// uniform float exampleUniform;

out vec4 fragColor;
void main()
{
	// vec4 color = texture(sTD2DInputs[0], vUV.st);
	vec4 color = vec4(1.0);
	fragColor = TDOutputSwizzle(color);
}

```

{% hint style="info" %}
Get the first input with **texture\(sTD2DInputs\[0\], vUV.st\)**
{% endhint %}

{% hint style="info" %}
**fragColor** is the final RGBA output color.
{% endhint %}

{% hint style="info" %}
**TDOutputSwizzle** is a cross platform check for some edge cases.
{% endhint %}

### **Uniforms**

Uniforms are variables. You can pass CHOP values into a GLSL TOP by a python reference of the CHOP on the second tab called Vectors, under the first value of the first parameter "Uniform Name 0". Call it something then update the GLSL code by replacing "exampleUniform" with your variable name.

```text
uniform float value;
uniform vec2 xy;
uniform vec3 rgb;
uniform vec4 rgba;
uniform bool toggle;
```

{% hint style="info" %}
Float values automatically gets converted to bools,  
by checking if the value is above zero.
{% endhint %}

## Tutorial

{% page-ref page="tutorial-noise-plane.md" %}

A lot of good info can be found in this epic article by Derivative: [Write a GLSL TOP](https://docs.derivative.ca/Write_a_GLSL_TOP)

