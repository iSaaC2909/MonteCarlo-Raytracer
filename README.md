# Monte Carlo Raytracer

A physically-based renderer implementing various global illumination techniques including Monte Carlo path tracing, photon mapping, and caustics rendering.

## Features

- **Multiple Rendering Techniques**:
  - Monte Carlo Path Tracing
  - Photon Mapping
  - Caustics Rendering
  - Whitted-style Ray Tracing

- **Material System**:
  - Diffuse (Lambertian) surfaces
  - Specular reflections
  - Transparent materials with refraction
  - Oren-Nayar BRDF for rough surfaces
  - Fresnel effects for realistic material transitions

- **Advanced Lighting**:
  - Global illumination
  - Area lights
  - Soft shadows
  - Caustics
  - Indirect lighting

- **Performance Optimizations**:
  - OpenMP parallel processing
  - KD-tree acceleration for photon mapping
  - Octree spatial partitioning for mesh rendering
  - Russian Roulette path termination

## Requirements

- CMake (minimum version 2.8)
- C++ compiler with OpenMP support (GCC 5 recommended)
- GLM library (included in external_libraries)

## Building the Project

1. Create a build directory:
```bash
mkdir build
cd build
```

2. Generate build files with CMake:
```bash
cmake ..
```

3. Build the project:
```bash
make
```

## Usage

Run the raytracer with a scene file as argument:

```bash
./global_illumination scene_file.xml
```

The renderer supports the following parameters (configurable in main.cpp):
- Image resolution (default: 1024x768)
- Number of samples for:
  - Caustics (default: 10)
  - Monte Carlo path tracing (default: 500)
  - Direct specular reflections (default: 100)
- Number of photons for photon mapping (default: 2,000,000)

## Scene Format

Scenes are defined in XML format and can include:
- Camera settings (position, direction, field of view)
- Light sources (position, color, intensity)
- Objects (meshes, spheres, planes)
- Materials (diffuse color, specular reflection, transparency, roughness)

## Implementation Details

### Camera
- Supports arbitrary positioning and orientation
- Configurable field of view
- Sub-pixel sampling for anti-aliasing

### Materials
- Diffuse reflectance with optional roughness (Oren-Nayar model)
- Specular reflections with configurable reflectance
- Transparent materials with refraction index
- Fresnel effects for realistic material transitions

### Light Transport
- Bidirectional path tracing
- Photon mapping for caustics and global illumination
- Russian Roulette for path termination
- Importance sampling for efficient rendering

### Acceleration Structures
- KD-tree for photon map storage and lookup
- Octree for mesh intersection optimization
- Möller–Trumbore algorithm for triangle intersection

## Output

The renderer outputs images in PPM format with:
- High dynamic range rendering
- Gamma correction
- Progress reporting during rendering
- Render time estimation

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests. 
