Nota preliminar: el siguiente código fue utilizado para el desarrollo del proyecto de titulación: "Art challenges technology, technology inspires art: Una discusión sobre las problemáticas que rodean a la inteligencia artificial desde el desarrollo de una obra artística implementada a base de  redes generativas antagónicas (GANs)" en el que se desarrolló un video con los siguientes parámetros: 
params = {"scenes": "eternal feminine | big translucent women eyes | rivers of wine | black haired woman dancing in a dress made out of the starry night ", "scene_prefix": "astrophotography #pixelart | artstation art by Azat Nurgaleev | #conceptart eternal feminine |  ", "scene_suffix": "| satellite image:-1:-.95 | text:-1:-.95 | watermark:-1:-.95 | backyard telescope:-1:-.95 | map:-1:-.95", "interpolation_steps": 0, "steps_per_scene": 60100, "direct_image_prompts": "https://cdna.artstation.com/p/assets/images/images/055/587/008/medium/azat-nurgaleev-img-3144.jpg?1667306880", "init_image": "", "direct_init_weight": "", "semantic_init_weight": "", "image_model": "Limited Palette", "width": 1920, "height": 1080, "pixel_size": 1, "smoothing_weight": 0.02, "vqgan_model": "sflckr", "random_initial_palette": false, "palette_size": 6, "palettes": 9, "gamma": 1, "hdr_weight": 0.01, "palette_normalization_weight": 0.2, "show_palette": false, "target_palette": "", "lock_palette": false, "animation_mode": "3D", "sampling_mode": "bicubic", "infill_mode": "wrap", "pre_animation_steps": 100, "steps_per_frame": 50, "frames_per_second": 30, "direct_stabilization_weight": "", "semantic_stabilization_weight": "", "depth_stabilization_weight": "", "edge_stabilization_weight": "", "flow_stabilization_weight": "", "video_path": "", "frame_stride": 1, "reencode_each_frame": true, "flow_long_term_samples": 1, "translate_x": "-1700*sin(radians(1.5))", "translate_y": "0", "translate_z_3d": "(50+3*t)*sin(t/10*pi)**2", "rotate_3d": "[cos(radians(1.5)), 0, -sin(radians(1.5))/sqrt(2), sin(radians(1.5))/sqrt(2)]", "rotate_2d": "5", "zoom_x_2d": "0", "zoom_y_2d": "0", "lock_camera": true, "field_of_view": 60, "near_plane": 200, "far_plane": 8000, "file_namespace": "prototipo_1", "allow_overwrite": false, "display_every": 50, "clear_every": 0, "display_scale": 1, "save_every": 50, "backups": 5, "show_graphs": false, "approximate_vram_usage": false, "ViTB32": true, "ViTB16": false, "RN50": false, "RN50x4": false, "learning_rate": null, "reset_lr_each_frame": true, "seed": 3024054553251595568, "cutouts": 40, "cut_pow": 2, "cutout_border": 0.25, "border_mode": "clamp"}




# PyTTI-Tools Documentation and Tutorials

[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://pytti-tools.github.io/pytti-book/intro.html)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pytti-tools/pytti-notebook/blob/main/pyttitools-PYTTI.ipynb)
[![DOI](https://zenodo.org/badge/461043039.svg)](https://zenodo.org/badge/latestdoi/461043039)
[![DOI](https://zenodo.org/badge/452409075.svg)](https://zenodo.org/badge/latestdoi/452409075)


## Requirements

    pip install jupyter-book
    pip install ghp-import

## Building and publishing

    # Add a new document to the book
    git add NewArticle.ipynb
    
    # The page won't show up unless you specify where it goes in the TOC
    git add _toc.yml
    git commit -am "Added NewArticle.ipynb"
    jupyter-book build .
    ghp-import -n -p -f _build/html
