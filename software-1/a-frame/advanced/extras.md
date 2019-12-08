# Particles

Ever heard the concept of particles in CGI? It's an amazing thing that allows us to create the illusion of rain, snow, fire, dust and much more. In A-Frame you can easily get started by including the [A-Frame Particle System](https://www.npmjs.com/package/aframe-particle-system-component) script!

```markup
<script src="https://unpkg.com/aframe-particle-system-component@1.0.x/dist/aframe-particle-system-component.min.js"></script> 
```

And then add the attribute _particle-system_ along with some parameters and off you go!

```markup
<a-entity particle-system="color: #EF0000,#44CC00"></a-entity>
```

The particle system comes with plenty of default values but you are encouraged to play around and tweak them!

| Property | Description | Default |
| :--- | :--- | :--- |
| preset | Preset configuration. Possible values are: `default`, `dust`, `snow`, `rain`. | `default` |
| maxAge | The particle's maximum age in seconds. | `6` |
| positionSpread | Describes this emitter's position variance on a per-particle basis. | `0 0 0` |
| type | The default distribution this emitter should use to control its particle's spawn position and force behaviour. Possible values are `1` \(box\), `2` \(sphere\), `3` \(disc\) | 1 \(box\) |
| rotationAxis | Describes this emitter's axis of rotation. Possible values are `x`, `y` and `z`. | `x` |
| rotationAngle | The angle of rotation, given in radians. `Dust` preset is `3.14`. | `0` |
| rotationAngleSpread | The amount of variance in the angle of rotation per-particle, given in radians. | `0` |
| accelerationValue | Describes this emitter's base acceleration. | `0, -10, 0` |
| accelerationSpread | Describes this emitter's acceleration variance on a per-particle basis. | `10 0 10` |
| velocityValue | Describes this emitter's base velocity. | `0 25 0` |
| velocitySpread | Describes this emitter's acceleration variance on a per-particle basis. | `10 7.5 10` |
| dragValue | Number between 0 and 1 describing drag applied to all particles. | `0` |
| dragSpread | Number describing drag variance on a per-particle basis. | `0` |
| dragRandomise | WHen a particle is re-spawned, whether it's drag should be re-randomised or not. Can incur a performance hit. | `false` |
| color | Describes a particle's color. This property is a "value-over-lifetime" property, meaning an array of values can be given to describe specific value changes over a particle's lifetime. | `#0000FF,#FF0000` |
| size | Describes a particle's size. | `1` |
| direction | The direction of the emitter. If value is `1`, emitter will start at beginning of particle's lifecycle. If value is `-1`, emitter will start at end of particle's lifecycle and work it's way backwards. | `1` |
| duration | The duration in seconds that this emitter should live for. If not specified, the emitter will emit particles indefinitely. | `null` |
| enabled | When `true` the emitter will emit particles, when `false` it will not. This value can be changed dynamically during a scene. While particles are emitting, they will disappear immediately when set to `false`. | `true` |
| particleCount | The total number of particles this emitter will hold. NOTE: this is not the number of particles emitted in a second, or anything like that. The number of particles emitted per-second is calculated by particleCount / maxAge \(approximately!\) | `1000` |
| texture | The texture used by this emitter. | `./images/star2.png` |
| randomise | When a particle is re-spawned, whether it's position should be re-randomised or not. Can incur a performance hit. | `false` |
| opacity | Either a single number to describe the opacity of a particle. |  |

