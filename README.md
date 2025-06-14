<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Registro de Asistencia</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      color: #333;
      background: #f5f5f5;
    }
    .container {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 12px rgb(0 0 0 / 0.1);
      max-width: 500px;
      margin-bottom: 20px;
    }
    .container h1 {
      color: #4caf50;
      margin-bottom: 20px;
    }
    label {
      font-weight: bold;
      margin-bottom: 10px;
      display: block;
    }
    input, select, button {
      padding: 10px;
      margin-bottom: 20px;
      width: 100%;
      border-radius: 6px;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }
    button {
      background: #4caf50;
      color: #fff;
      font-size: 16px;
      border: none;
      transition: background 0.3s ease-in-out;
      cursor: pointer;
    }
    button:hover {
      background: #45a049;
    }
  </style>
</head>
<body>

<h1>Registro de Asistencia</h1>

<div class="container">
  <p>Cuando seleccionamos el perfil del docente o el mismo docente selecciona su perfil para poder marcar su asistencia se verá los siguientes puntos correspondientes del boceto.</p>

  <p>Así mismo se podrá marcar la fecha de asistencia del mismo día del cual este ingrese a marcar su asistencia; de lo contrario, si no marca los días anteriores se mandará un aviso a la GRELL.</p>

  <p>Al registrar su asistencia automáticamente será guardada y enviada a la base de datos, por el contrario si no hay asistencia tendrá que justificar el porqué no asistió al colegio.</p>

  <h2>Marcar Asistencia</h2>

  <form id="formAsistencia">
    <label for="perfil">Seleccione el perfil del profesor</label>
    <select id="perfil" name="perfil">
      <option value="">Seleccione</option>
      <option value="profesor1">Profesor 1</option>
      <option value="profesor2">Profesor 2</option>
      <option value="profesor3">Profesor 3</option>
    </select>

    <label for="fecha">Fecha de asistencia</label>
    <input id="fecha" name="fecha" type="date" />

    <label for="justificacion">Justificación (si falta)</label>
    <input id="justificacion" name="justificacion" type="text" placeholder="Ingrese justificación si falta" />

    <button type="submit">Marcar asistencia</button>
  </form>

</div>

<script>
  document.getElementById('formAsistencia').addEventListener('submit',(e)=>{
    e.preventDefault();

    const perfil = document.getElementById('perfil').value.trim();
    const fecha = document.getElementById('fecha').value.trim();
    const justificacion = document.getElementById('justificacion').value.trim();

    if (perfil === '' || fecha === '') {
      alert('Debe completar el perfil y la fecha.');
      return;
    }

    if (justificacion === '' && new Date(fecha) < new Date()) {
      alert('Debe proporcionar una justificación por falta de asistencia.');
      return;
    }

    // Aquí se guardaría en la base de datos
    console.log('Registro guardado!', {
      perfil,
      fecha,
      justificacion
    });

    alert('Registro guardado con éxito.');
    e.target.reset();

  });
</script>

</body>
</html>
