# --- Algorithms ---
### Function fractalNoise()
    Example 
        let s = getSpace();
        let scale = .2;
        let amplitude = .9;
        let speed = 0.1 * time;
        let n = fractalNoise(s * amplitude + speed) * scale;
        sphere(0.3);
        expand(n);
    Description : Computes mutliple octaves of 3D simplex noise. Syntax : ```js fractalNoise(position) ```Parameters  :**position** vec3: the position to sample noise
### Function noise()
    Noise Basic
     Example 
        let scale = 2.0;
        let s = getSpace();
        let n = noise(scale * s);
        sphere(0.7 + n);
    Noise Color
     Example
        let noiseScale = 5.0;
        let s = getSpace();
        let n = 0.5 * noise(noiseScale * s + time) + 0.5;
        color(n,n,n);   
        sphere(0.7);
    Description : Computes 3D simplex noise. Syntax : ```js noise(position) ```Parameters  :**position** vec3: the position to sample noise
### Function sphericalDistribution()
    Spherical Distribution
    Example 
        let s = getSpace();
        sphere(0.5);
        let numPoints = input(40, 0, 100);
        let distro = sphericalDistribution(s,  numPoints);
        expand(distro.w * 0.5);
        Spherical Distribution 2
    Example 
        let s = getSpace();
        sphere(0.5);
        let numPoints = input(40, 0, 100);
        let distro = sphericalDistribution(s, numPoints);
        expand(distro.w * -0.4);
    Description : Computes the distance to the nearest of N points distributed over a sphere. Syntax : ```js sphericalDistribution(p, numPoints) ```Parameters  :**p** vec3: a point to sample. **numPoints** Float: number of points distributed on the sphere. ### Returns Vec4: x,y,z is the location of the point nearest to p, and w is the distance to that point ( w = distance(xyz,p) )

# --- Color ---

### Function color()
    Example 
    displace(-0.3, 0, 0);
    color(0.1, 1.0, 1.0);
    sphere(0.2);
    // Alternatively
    //translate the coordinate space to the right
    displace(0.6, 0, 0);
    let color2 = vec3(1, 0.2, 0.2);
    color(color2);
    sphere(0.2);
     Description : Applies a color to all objects created after with the provided red, green and blue values. Syntax : ```js color(red, green, blue); ```Parameters  :**red** Float: value from 0.0 to 1.0 **red** Float: value from 0.0 to 1.0 **green** Float: value from 0.0 to 1.0 **blue** Float: value from 0.0 to 1.0 
### Function fresnel()
    Example
        let f = fresnel(2);
        color(vec3(f));
        sphere(0.5);
    Description : Generates a radial gradient based on the camera direction that can be used to create edge glow. When used in reflections this technique will make something looked at straight on the least reflective and when turned nearly 90 degrees on edge the most reflective. More information can be found [here](https://www.dorian-iten.com/fresnel/) Syntax : ```js fresnel(value); ```Parameters  :**value** Float: amount Description : Converts Hue, Saturation, Value(also called Brightness) into RGB values. Syntax : ```js hsv2rgb(inputColor); ```Parameters  :**inputColor** Vec3: input hue, saturation, color values from 0.0 to 1.0 
### Function lightDirection()
    Example 
        lightDirection(0, 0, 1);
        //alternatively lightDirection(vec3(0, 0, 1));
        sphere(0.5);
    Description : Sets the direction of the built-in lighting. By default the light points from the top down as lightDirection(0, 1, 0). Syntax : ```js lightDirection(x, y, z); lightDirection(position); ```Parameters  :**x** Float: value from 0.0 to 1.0. Defaults to 0 **y** Float: value from 0.0 to 1.0. Defaults to 1 **z** Float: value from 0.0 to 1.0. Defaults to 0 **position** Vec3: defaults to vec3(0, 1, 0). 
### Function metal()
    Example 
        metal(.5);
        sphere(0.3);
    Description : Defines how metallic the shape should be. The default lighting in Shader Park in is based on [PBR](https://learnopengl.com/PBR/Lighting) which provides a metallic property. Syntax : ```js metal(value); ```Parameters  :**value** Float: value from 0.0 to 1.0. Defaults to ____ 
### Function mixMat()
    Example 
        color(0, 0, 1);
        box(vec3(.4));
        mixMat(.5);
        color(1, 0, 0);
        sphere(0.5);
    Description : Mix between two materials. Works with [color()](/references-js/color/color.html), [metal()](/references-js/color/metal.html), and [shine()](/references-js/color/shine.html) Syntax : ```js mixMat(amount); ```Parameters  :**amount** Number: value from 0 to 1.0 to mix 
### Function noLighting()
    Example 
        noLighting();
        color(.7, .7, .7);
        sphere(0.5);
    Description : Turns off the default lighting. Syntax : ```js noLighting(); ``` 
### Function occlusion()
    Example 
        sphere(0.3);
        occlusion(.8);
        displace(0, -.8, 0);
        box(1, .5, 1);
    Description : Approximates the soft shadows. Syntax ```js occlusion(amount); ``` Parameters : **amount** Float: value form 0.0 to 1.0 
### Function rgb2hsv()
    Example 
        // Define color and draw reference sphere
        let red = vec3(0.9,0.0,0.0);
        color(red);
        displace(-0.3,0.0,0.0);
        sphere(0.2);
        // Convert color to HSV
        let hsv = rgb2hsv(red);
        // Shift hue
        hsv.x += time*0.2;
        // Convert back to RBG
        let shifted = hsv2rgb(hsv);
        // Draw second sphere with shifted hue
        color(shifted);
        displace(0.6,0.0,0.0);
        sphere(0.2);
    Description : Converts RGB values into Hue, Saturation, Value(also called Brightness). Syntax : ```js rgb2hsv(inputColor); ``` Parameters : **inputColor** Vec3: input red, green, and blue color values from 0.0 to 1.0
### Function shine()
    Example 
        shine(.8);
        sphere(0.5);
    Description : Defines how shiny the shape should be. In other 3D modeling applications the term albedo might be used instead of shine. The default lighting in Shader Park is based on [PBR](https://learnopengl.com/PBR/Lighting) which provides a albedo property. Syntax : ```js shine(value); ``` Parameters : **value** Float: value from 0.0 to 1.0. Defaults to 

# --- Geometries ---
### Function box()
    Example 
        box(0.3, 0.3, 0.3);
    Description : Draw a box with the given width, height, and depth Syntax : ```js box(width, height, depth); ``` Parameters : **width** Number: width of the box **height** Number: height of the box **depth** Number: depth of the box --- Syntax : ```js box(size); ``` Parameters : **size** Vec3: width, height and depth of the box.
### Function boxFrame()
    Example 
        boxFrame(vec3(.4), .02);
    Description : Draw a boxFrame with the given size and thickness Syntax : ```js boxFrame(size, thickness); ``` Parameters : **size** Vector3: size of the boxframe **thickness** Float: thickness of the frame 
### Function cylinder()
    Example 
        cylinder(0.3, 0.3);
    Description : Draw a cylinder with the given radius, and height Syntax : ```js cylinder(radius, height); ``` Parameters : **radius** Number: radius of the box **height** Number: height of the box Syntax : ```js cylinder(size) ``` Parameters : **size** vec3: radius, and height 
### Function grid() 
    Example 
    grid(2, .2, .04);
    Description : Draw a 3D grid, helpful for visualizing/debugging space distortions. Syntax : ```js grid(count, scale, thickness); ``` Parameters : **count** Number: number of grid sections. ranges from 0 to any number **scale** Float: size of the grid sections **thickness** Float: thickness of the grid sections
### Function line()
    Example 
        let pos1 = vec3(-0.2, -0.2, -0.2);
        let pos2 = vec3(0.2, 0.2, 0.2);
        line(pos1, pos2, 0.02);
    Description : Draw a line between the given start and end position with the given line thickness Syntax : ```js line(startPosition, endPosition, thickness); ``` Parameters : **startPosition** Vec3: x, y, and z starting position of the line **endPosition** Vec3: x, y, and z ending position of the line **thickness** Float: thickness of the line To generate geometry we can use signed distance field operations. For info on how these functions work under the hood look at IQ's examples
### Function shape()
    Example
        let purpleSphere = shape(() => {
          color(1, 0, 1);
          displace(.4, .4, 0);
          sphere(0.2);
        });
        purpleSphere();
        sphere(0.2);
    Example 2  
        //since shape returns a funciton you can call it right after it's defined
        shape(() => {
          color(1, 0, 1);
          displace(.4, .4, 0);
          sphere(0.2);
        })();
        sphere(0.2);
    Example 3 Shape + Construction Modes
        shape(() => {
          displace(0, 0, .4);
          box(.23, .23, .23);
          difference();
          sphere(.3);
        })();
        // without using shape mixGeo would just blend with the
        // previsouly defind object, in this case sphere(0.3);
        mixGeo(abs(sin(time)));
        sphere(0.33);
    Example 4 Parameters 
        // creates a box with a sphere cut out of the center
        // draws at the provided x, y
        let cutOut = shape((x, y) => {
          displace(x, y, 0);
          rotateX(time);
          rotateY(time);
          box(0.21, 0.21, 0.21);
          difference();
          sphere(0.27);
        });
        cutOut(.2, .2, time);
    Example 5 Higher Order Functions 
            // creates a box with a sphere cut out of the center
        // draws at the provided x, y and colors with the step
        let cutOut = shape((x, y, step) => {
          displace(x, y, 0);
          rotateX(time);
          rotateY(time);
          color(0, 1, step)
          box(0.21, 0.21, 0.21);
          difference();
          sphere(0.27);
        });
        blend(0.1);
        layoutCircle(cutOut, 4, .4);
    Description : Creates a new primitive shape. All state changing commands (color, displacement, geometry modes) are encapsulated and will only have an affect within scope of the provided function. Useful for isolating components with their own distortions and materials. Shapes can be nested for hierarchical modeling. Syntax : ```js shape(shape_func); ``` Parameters : **shape_func** Function: A function which draws a shape. ### Returns Function: An encapsulated version of shape_func which will not modify any drawing state outside of its own scope. Note: Any arguments given to this function will be forwarded as arguments to shape_func.
### Function sphere()
    Example 
        sphere(0.3);
    Description : Draw a sphere with given size Syntax : ```js sphere(size); ``` Parameters : **size** Number: size of the sphere
### Function torus()
    Example 
        rotateX(Math.PI/2);
        torus(0.3, 0.08);
    Description : Draw a torus with the given outer ring size and inner ring size Syntax : ```js torus(outerRingSize, innerRingSize); ``` Parameters : **outerRingSize** Number: size of the outer ring **innerRingSize** Number: size of the inner ring 

# --- Global Settings ---

### Function setGeometryQuality()
    Example 
        setGeometryQuality(80);
        sphere(0.5);
        let s = getSpace();
        let n = noise(s*10);
        expand(n*.2);   
    Description : As you distort the surface of any of the objects you create you may notice artifacting. To get rid of this you can use a higher Geometry Quality, but at the cost of performance. This function provides the same functionality as [setStepSize](/references-js/global-settings/setStepSize.html). Syntax : ```js setGeometryQuality(size); ``` Parameters : **size** Float: value from 0 to 100. Defaults to 15;
### Function setMaxIterations()
    Example <!-- --> Description : Sets the number of loops that are performed while raymarching(the underlying technique that allows us to render 3D shaders). Decreasing this number will speed up the rendering, but may cause artifacts. Increasing the number will slow down the rendering, but may improve the quality. You may want to combine this with [setStepSize()]((/references-js/global-settings/setStepSize.html)) to get a good balance. Syntax : ```js setMaxIterations(iterations); ``` Parameters : **iterations** Int: value from 0 to any value.
### Function setStepSize()
    Example 
        setStepSize(.13);
        sphere(0.5);
        let s = getSpace();
        let n = noise(s*10);
        expand(n*.2);
    Description : As you distort the surface of any of the objects you create you may notice artifacting. To get rid of this you can use a smaller step size, but at the cost of performance. This function provides the same functionality as [setGeometryQuality](/references-js/global-settings/setGeometryQuality.html), but is provided as a short hand for anyone with previous raymarching experience. The raymarching engine that powers Shader Park uses an algorithm called sphere tracing. In this process a ray / photon is marched forwards from the camera's perspective towards the current scene. The size of the step is determined from setStepSize(). If the value is really small the engine must take many more steps as it calculates the distance to the surface of the object. This will provide more detail, but it is calculated for every pixel, which can dramatically slow down the performance. A great breakdown of the how raymarching works can be found [here](https://www.youtube.com/watch?v=Cp5WWtMoeKg) (Note the example in the video uses GLSL and is built in Unity). Syntax : ```js setStepSize(size); ``` Parameters : **size** Float: value from 0.0 to 1.0. Defaults to 0.85; 

# --- GLSL ---

### Function glslFunc() 
    Example 
        let branchingColor = glslFunc(`
        vec3 test(vec3 mouse, vec3 col1, vec3 col2) {
        	if(mouse.x <0.) {
            	return col1;
        	} else {
            	return col2;
            }
        }
        `);
        let col = branchingColor(mouse, vec3(0, 1, 0), vec3(1, 0, 0));
        color(col);
        sphere(.5);
     Example 2 Custom Color + Shape Extrusion
        let koch = glslFunc(`
        //https://www.shadertoy.com/view/Mlf3RX
        float koch(vec2 p)
        {
            float ft = mod(floor(time),6.)+1.;
            p = abs(fract(p)-0.5);
            for(int i=0;i<12;++i)
            {
                if (floor(float(i)*.5) > ft)break; //"animation"
        		if(time == 0.0) {
                p += vec2(p.y*1.735, -p.x*1.735);
                p.x = abs(p.x)-0.58;
                p = -vec2(-p.y, p.x)*.865;
                } else {
                  p = -vec2(-p.y + p.x*1.735, abs(p.x + p.y*1.735) - 0.58)*.865; //One loc version
                }
            }
            return mod(floor(time*2.),2.)>0. ? abs(p.x)/(ft*ft)*14. : p.x/(ft*ft)*16.;
            //return p.x;
        }
        `);
        rotateX(PI/2);
        let s= getSpace();
        let col = koch(vec2(s.x, s.z));
        color(pow(vec3(col), vec3(.1))+normal)
        sphere(col*.005+.5)
      Example 3 Custom Raymarcher
        let march = glslFunc(`
        struct Ray {
          vec3 origin;
          vec3 direction;
        };

        struct Sphere {
            vec3 position;
            float radius;
        };

        struct Plane {
        	vec3 normal;
            float offset;
        };
      Desription: Creates a javascript function from a GLSL function. This enables the ability to use if statements(branching),work with integers and even create your own raymarcher. Note this will not work with GL ES3. To use GL ES3 look at [glslFuncES3](/references-js/glsl/glslFuncES3.html) (note, the error handeling of the glsl is not nearly as good as the glslFunc). Syntax : ```js glslFunc(func); ``` Parameters : **func** String: a String containing a GLSL function. ### Returns Function: An encapsulated version of func. Any arguments given to this function will be forwarded as arguments to the provided glsl function. 
### Function glslFuncES3() 
    Example
    Example 2 Custom Color + Shape Extrusion
    Example 3 Custom Raymarcher
    Description : Creates a javascript function from a GLSL function. This enables the ability to use if statements(branching), work with integers and even create your own raymarcher. Note this will work with GL ES3, but does not have as nice of error handeling as [glslFunc](/references-js/glsl/glslFunc.html) Syntax : ```js glslFuncES3(func); ``` Parameters : **func** String: a String containing a GLSL function. ### Returns Function: An encapsulated version of func. Any arguments given to this function will be forwarded as arguments to the provided glsl function. 
### Function glslSDF() 
    Example
        let octahedron = glslSDF(`
        //https://iquilezles.org/articles/distfunctions/
        float sdOctahedron( vec3 p, float s){
          p = abs(p);
          float m = p.x+p.y+p.z-s;
          vec3 q;
               if( 3.0*p.x < m ) q = p.xyz;
          else if( 3.0*p.y < m ) q = p.yzx;
          else if( 3.0*p.z < m ) q = p.zxy;
          else return m*0.57735027;

          float k = clamp(0.5*(q.z-q.y+s),0.0,s); 
          return length(vec3(q.x,q.y-s+k,q.z-k)); 
        }`);

        octahedron(.6);
    Example 2  
        let hollowCutSphere = glslSDF(`
        //https://www.shadertoy.com/view/7tVXRt
        float sdCutHollowSphere( vec3 p, float r, float h, float t )
        {
          // sampling independent computations (only depend on shape)
          float w = sqrt(r*r-h*h);

          // sampling dependant computations
          vec2 q = vec2( length(p.xz), p.y );
          return ((h*q.x<w*q.y) ? length(q-vec2(w,h)) : 
                                  abs(length(q)-r) ) - t;
        }
        `);


        rotateZ(PI/2);
        hollowCutSphere(.5, sin(time)*.5, .02);
    Example 3 
        let hexPrism = glslSDF(`
        //https://iquilezles.org/articles/distfunctions/
        float sdHexPrism( vec3 p, vec2 h ){
          const vec3 k = vec3(-0.8660254, 0.5, 0.57735);
          p = abs(p);
          p.xy -= 2.0*min(dot(k.xy, p.xy), 0.0)*k.xy;
          vec2 d = vec2(
               length(p.xy-vec2(clamp(p.x,-k.z*h.x,k.z*h.x), h.x))*sign(p.y-h.x),
               p.z-h.y );
          return min(max(d.x,d.y),0.0) + length(max(d,0.0));
        }`);

        hexPrism(vec2(.2, .2));
    Description : Generates an primitive from the provided GLSL function. The provided GLSL function must return a float(the distance filed) and the first parameter must be a vec3(position). This will not work with GL ES3. Syntax : ```js glslSDF(glslCode); ``` Parameters : **glslCode** String: The glsl source code. ### Returns Function: A js function of the glslCode. Any arguments given to this function will be forwarded as arguments to the provided glsl function. 

# --- Input ---

### Function getRayDirection() 
    Example 
        let ray = getRayDirection();
        rotateX(ray.x * 4);
        box(0.5, .5, .5);
    Please move the camera around for these examples
    Description : Gets the direction that camera / ray is looking at. This can be helpful to add interaction based off the camera position. Syntax : ```js getRayDirection(); ``` ### Returns Vec3: direction the camera is pointing. 
### Function getSpace() 
    Example 
        let s = getSpace();
        setSpace(s - vec3(.5, .5, 0));
        sphere(0.5);
    Description : Gets the current coordinate space. When combining operations it can be helpful to get a reference to an unchanged coordinate space. Calling getSpace() inside [shape()](/references-js/geometries/shape.html) returns a new reference to the space at the current scope. Syntax : ```js getSpace(); ``` ### Returns Vec3: The current coordinate space
### Function input() 
    Example 
        let size = input(0.3);
        sphere(size);
    Description : Creates an input slider defaulting to the provided starting value that ranges from the given minimum and maximum values. Internally a uniform is created for your input slider, which allows the value to be updated without re-compiling the shader. Syntax : ```js input(startValue, minValue, maxValue); input(startValue); input(); ``` Parameters : **startValue** Float: the initial value. Defaults to 0. **minValue** Float: the minimum range of the slider input. Defaults to 0. **maxValue** Float: the maximum range of the slider input. Defaults to 1.0. 
### Function mouse 
    Example 
        // alternatively
        // dispace(mouse.x, mouse.y, mouse.z);
        displace(mouse);
        sphere(0.3);
    Description : mouse contains the current x, y, and z position of the cursor relative to (0, 0, 0) in the center of the scene. Syntax : ```js mouse mouse.x mouse.y mouse.z ```
### Function mouseIntersection() 
    Example 
        let  s = getSpace();
        let dotSize = pow(distance(s, mouseIntersection())*10, 20)+.1;
        let dotColor = vec3(.1, abs(sin(time)), abs(cos(time)));
        let col =  dotColor/dotSize;
        color(col);
        sphere(0.4);
    Description : Provides the location where the mouse intersects the drawn shape. Syntax : ```js mouseIntersection(); ``` ### Returns Vec3: The position of the mouse intersection. 
### Function normal() 
    Example 
        color(normal.x, normal.y, normal.z);
        sphere(0.4);
    Description : The vector which points directly out of the geometry's surface. Note: Only has an effect on color, cannot be used to influence geometry. Syntax : ```js normal normal.x normal.y normal.z ```
### Function time
    Example 
        let oscillation = abs(sin(time));
        let endSize = 0.5;
        sphere(endSize * oscillation);
    Description : Time is passed in by default which can be used for animation. Time is incremented every new frame that is drawn and is scaled to milliseconds. Syntax : ```js time ``` 

# --- Math ---

### Function toSpherical() 
    Example toSpherical simple
        rotateY(PI);
        let s = toSpherical(getSpace());
        color(vec3((s.z+PI)/TAU));
        sphere(0.5);
    Example Spherical basic II
        function oscillate(x) {
         	return sin(24*x)*0.5;
        }
        let s = toSpherical(getSpace());
        let m = min(oscillate(s.y),oscillate(s.z));
        color(vec3(m+0.5));
        sphere(0.5);
        expand(0.02*m);
    Description : Gets the spherical coordinates form the provided space. This function is commonly used with [getSpace()](/references-js/input/getSpace.html). Syntax : ```js toSpherical(space); ``` Parameters : **space** Vec3: coordinate space ### Returns Vec3: spherical coordinate space 

# --- Operations  ---

### Function blend() 
    Example 
        blend(0.23);
        displace(-0.25, 0, 0);
        box(0.2, 0.2, 0.2);
        displace(0.5, 0, 0);
        sphere(0.2);
    Description : Blend between two geometries by the provided amount. Syntax : ```js blend(amount); ``` Parameters : **amount** Number: value from 0 to 1.0 to blend 
### Function difference() 
    Example 
        box(0.3, 0.3, 0.3);
        difference();
        sphere(0.38);
    Description : Subtract one geometry form another. Syntax : ```js difference(); ``` 
### Function displace() 
    Example
        displace(0.4,0.0,0.0);
        sphere(0.3);
    Description : Translate, or distort the coordinate space by the given positions. Transformations are cumulative and apply to everything that happens after and subsequent calls to the function accumulates the effect. For example, calling displace(.2, 0, 0) and then displace(.2, 0, 0) is the same as displace(.4, 0, 0). The coordinate space can be set back to default by calling reset(). This function can be further controlled by using the shape(). Syntax : ```js displace(xPosition, yPosition, zPosition); displace(position); ` 
### Function expand() 
    Example 
        box(0.2, 0.2, 0.2);
        expand(0.1);
    Description : Expand a geometry by the provided amount. Useful for creating rounded edges. Syntax : ```js expand(amount); ``` Parameters : **amount** Number: value from 0 to 1.0 to expand by 
### Function intersect() 
    Example 
        box(0.3, 0.3, 0.3);
        intersect();
        sphere(0.38);
    Description : Display the intersection of two geometries. Syntax : ```js intersect(); ``` 
### Function  mirrorN() 
    Example 
        mirrorN(3, .13);
        sphere(.1);
    Description : Mirror all operations along the x, y, and z axis N number of times with the given spacing. Syntax : ```js mirrorN(count, spacing); ``` Parameters : **count** Number: the number of times to mirror the space. Ranges from 0 to any number **spacing** Float: how much spacing to put between each mirror. 
### Function mirrorX() 
    Example 
        mirrorX();
        displace(0.2, 0.0, 0.0);
        sphere(0.15);
    Description : Mirror all operations along the x-axis. Syntax : ```js mirrorX(); ```
### Function mirrorXYZ() 
    Example 
        mirrorXYZ();
        displace(0.2, 0.2, 0.2);
        sphere(0.15);
    Description : Mirror all operations along the x, y, and z axis. Syntax : ```js mirrorXYZ(); ``` 
### Function mirrorY() 
    Example 
        mirrorY();
        displace(0, 0.2, 0);
        sphere(0.15);
    Description : Mirror all operations along the y-axis. Syntax : ```js mirrorY(); ```
### Function mirrorZ() 
    Example 
        mirrorZ();
        displace(0, 0.0, 0.2);
        sphere(0.15);
    Description : Mirror all operations along the z-axis. Syntax : ```js mirrorZ(); ```
### Function  mixGeo() 
    Example 
        sphere(0.3);
        mixGeo(abs(sin(time)));
        box(0.3, 0.3, 0.3);
    Description : Mix between two geometries. Syntax : ```js mix(amount); ``` Parameters : **amount** Number: value from 0 to 1.0 to mix 
### Function reset() 
    Example 
        displace(0.4, 0, 0);
        sphere(0.2);
        reset();
        box(0.2, 0.2, 0.2);
    Description : Reset the coordinate space back to (0, 0, 0) after it has been translated, or distorted using [displace](/references-js/operations/displace.html), [mirror](/references-js/operations/mirrorX.html), or [rotate](/references-js/operations/rotateX.html). Syntax : ```js reset(); ```
 ### Function rotateX() 
    Example 
        rotateX(PI/2);
        torus(0.4, 0.2);
    Description : Rotate the coordinate space around x-axis. Syntax : ```js rotateX(amount); ```Parameters :**amount** Number: value in radians, which can rotate a full 360° by providing a value from -PI/2 to PI/2 
 ### Function rotateY()
    Example 
        rotateY(time);
        box(0.2, 0.2, 0.2);
    Description : Rotate the coordinate space around y-axis. Syntax : ```js rotateY(amount); ```Parameters :**amount** Number: value in radians, which can rotate a full 360° by providing a value from -PI/2 to PI/2 
### Function rotateZ() 
    Example 
        rotateZ(time);
        box(0.2, 0.2, 0.2);
    Description : Rotate the coordinate space around z-axis. Syntax : ```js rotateZ(amount); ```Parameters :**amount** Number: value in radians, which can rotate a full 360° by providing a value from -PI/2 to PI/2
### Function setSDF() 
    Example --- Description : Directly sets the distance field value. Syntax : ```js setSDF(distance); ``` Parameters : **distance** Float: The distance from the current position to the geometry's surface. 
### Function setSpace() 
    Example
        let s = getSpace();
        setSpace(s - vec3(.5, .5, 0));
        sphere(0.5);
    Example 2
        let s = getSpace();
        setSpace(s * vec3(1, .7, 1));
        sphere(0.5);
    Description : Used for applying any kind of space transformation. This includes translating the coordinate space, or stretching / warping the space the objects reside in. This function can be used to recreate similar functionality to [displace()](/references-js/operations/displace.html), however if you scale the coordinate space using displace it will also translate the object. It's commonly used setSpace with [getSpace()](/references-js/input/getSpace.html). Syntax : ```js setSpace(space); ``` Parameters : **space** Vec3: coordinate space
### Function shell()
    Example 
        lightDirection(0, 0.2, 0.2);
        sphere(0.3);
        shell(0.02);
        displace(0.2, 0.2, 0.2);
        difference();
        box(0.2, 0.2, 0.2);
    Description : Hollow out a shape and creates a shell around with the provided thickness. Syntax : ```js shell(thickness); ``` Parameters : **thickness** Number: value from 0.001 to .2
### Function union() 
    Example
        union();
        sphere(0.25);
        box(0.2, 0.2, 0.2); 
    Description : New geometry will be added it to the scene. Union is applied by default. Syntax : ```js union(); ``` 

# Functions 

### toSpherical(space); 
    Parameters Vec3: coordinate space
### blend(amount); 
    Parameters amount Number: value from 0 to 1.0 to blend
### difference();  
    subtract the geometry from the scene
### displace(xPosition yPosition zPosition);
    Parameters xPosition Number: x coordinate space yPosition Number: y coordinate space zPosition Number: z coordinate space
### displace(position);  
    Parameters position Vec3: coordinate space
### expand(amount);  
    Parameters amount Number: value from 0 to 1.0 to expand
### intersect();  
    intersect the geometry with the scene
### mirrorN(count spacing);  
    Parameters count Number: number of mirrors to create spacing Number: distance between mirrors
### mirrorX();  
    mirror all operations along the x-axis
### mirrorXYZ();  
    mirror all operations along the x y and z axis
### mirrorY(); 
    mirror all operations along the y-axis
### mirrorZ(); 
     mirror all operations along the z-axis
### mixGeo(amount);  
    Parameters amount Number: value from 0 to 1.0 to mix
### reset();
    reset the coordinate space back to (0 0 0) after it has been translated or distorted using displace mirror or rotate
### rotateX(amount);
    amount Number: value in radians which can rotate a full 360° by providing a value from -PI/2 to PI/2
### rotateY(amount)  
    amount Number: value in radians which can rotate a full 360° by providing a value from -PI/2 to PI/2
### rotateZ()  
    amount Number: value in radians which can rotate a full 360° by providing a value from -PI/2 to PI/2
### setSDF(distance);  
    Parameters distance Float: The distance from the current position to the geometry's surface.
### setSpace(space);  
    Parameters space Vec3: coordinate space
### shell(thickness);  
     thickness Number: value from 0.001 to .2
### union();  
    Combine two or more geometry together
### box(width height depth)  
    width Number: width of the sculpture value from 0 to 1.0 height Number: height of the sculpture value from 0 to 1.0 depth Number: depth of the          sculpture value from 0 to 1.0
### boxFrame(size thickness)  
    size Number: size of the box frame value from 0 to 1.0 thickness Number: thickness of the box frame value from 0 to 1.0
### cylinder(radius height)  
    radius Number: radius of the sculpture value from 0 to 1.0 height Number: height of the sculpture value from 0 to 1.0
### grid(count scale thickness);  
     count Number: number of grid lines scale Number: distance between grid lines thickness Number: thickness of the grid lines
### line(startPosition endPosition thickness);  
    startPosition Vec3: starting position of the line endPosition Vec3: ending position of the line thickness Number: thickness of the line
### shape(shape_func);  
    shape_func Function: function that returns a number
### sphere(size);  
    size Number: size of the sphere value from 0 to 1.0
### torus(outerRingSize innerRingSize);  
    outerRingSize Number: size of the outer ring value from 0 to 1.0 innerRingSize Number: size of the inner ring value from 0 to 1.0
### setGeometryQuality(size);  
    size Number: size of the geometry value from 0 to 1.0
### setMaxIterations(iterations);  
    iterations Number: number of iterations value from 0 to 100
### setStepSize(size);  
    size Number: size of the step value from 0 to 1.0
### glslFunc(func);  
    func String: glsl function
### glslFuncES3(func);  
    func String: glsl function
### glslSDF(glslCode);   
    glslCode String: glsl code
### getRayDirection();  
    Returns Vec3: direction of the ray
### getSpace();   
    Returns Vec3: coordinate space
### input(startValue minValue maxValue);  
    startValue Number: starting value minValue Number: minimum value maxValue Number: maximum value
### input(startValue);  
    startValue Number: starting value
### input();   
    Returns Number: value from 0 to 1.0
### mouse
    Returns Vec3: mouse position
### mouse.x
    Returns Number: mouse x position
### mouse.y
    Returns Number: mouse y position
### mouse.z 
    Returns Number: mouse z position
### mouseIntersection();   
    Returns Vec3: mouse intersection
### normal() 
    Returns Vec3: normal
### time
    Returns Number: time
