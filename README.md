# Boda-fotos
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fotos de Nuestra Boda</title>
  <style>
    body { font-family: sans-serif; background: #f9f9f9; margin: 0; padding: 20px; }
    header { text-align: center; padding: 40px 0; background: #fff; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
    h1 { margin: 0; font-size: 2.5em; }
    form { max-width: 500px; margin: 40px auto; background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
    input, textarea { width: 100%; margin: 10px 0; padding: 10px; font-size: 1em; border: 1px solid #ccc; border-radius: 5px; }
    button { padding: 10px 20px; font-size: 1em; background: #007BFF; color: #fff; border: none; border-radius: 5px; cursor: pointer; }
    button:hover { background: #0056b3; }
    .gallery { display: grid; grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 10px; padding: 20px; }
    .gallery img { width: 100%; border-radius: 10px; object-fit: cover; }
  </style>
</head>
<body>
  <header>
    <h1>Fotos de Nuestra Boda</h1>
    <p>Sube tus fotos favoritas para compartir con todos</p>
  </header>

  <form id="uploadForm">
    <input type="text" id="nombre" placeholder="Tu nombre" required />
    <textarea id="comentario" placeholder="Comentario (opcional)"></textarea>
    <input type="file" id="foto" accept="image/*" required />
    <button type="submit">Subir Foto</button>
  </form>

  <div class="gallery" id="galeria">
    <!-- Las imágenes se mostrarán aquí -->
  </div>

  <script>
    const form = document.getElementById('uploadForm');
    const galeria = document.getElementById('galeria');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      const fileInput = document.getElementById('foto');
      const nombre = document.getElementById('nombre').value;
      const comentario = document.getElementById('comentario').value;

      if (fileInput.files.length === 0) return alert("Por favor selecciona una foto.");

      const file = fileInput.files[0];
      const reader = new FileReader();
      reader.onload = function (event) {
        const img = document.createElement('img');
        img.src = event.target.result;
        galeria.appendChild(img);
        form.reset();
      };
      reader.readAsDataURL(file);
    });
  </script>
</body>
</html>
