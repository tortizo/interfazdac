<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Registro de Eventos</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdn.datatables.net/1.13.6/css/dataTables.bootstrap5.min.css">
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdn.datatables.net/1.13.6/js/jquery.dataTables.min.js"></script>
  <script src="https://cdn.datatables.net/1.13.6/js/dataTables.bootstrap5.min.js"></script>
  <style>
    body { font-family: 'Roboto','Open Sans', Arial, sans-serif; background-color: #ffffff; color: #1D2B4F; }
    .franja-superior { background-color: #1D2B4F; color: white; font-size: 22px; font-weight: bold; vertical-align: middle; }
    .franja-naranja { height: 10px; background-color: #F39200; }
    .course-container { background-color: #fff; padding: 30px; border-radius: 8px; box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); max-width: 800px; margin: auto; margin-top: 30px; margin-bottom: 30px; }
    h1 { color: #0056b3; text-align: center; margin-bottom: 30px; }
    .info-grid { display: grid; grid-template-columns: 1fr 2fr; gap: 15px; margin-bottom: 25px; align-items: center; }
    .info-grid label { font-weight: bold; color: #555; padding-right: 10px; }
    .info-grid input[type="text"], .info-grid input[type="date"], .info-grid select, .objective-text textarea, .content-program-text textarea {
      width: 100%; padding: 8px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box;
    }
    .section-title { background-color: #e2e2e2; color: #333; padding: 10px 15px; border-radius: 5px; margin-top: 20px; margin-bottom: 15px; font-weight: bold; }
    .objective-text, .content-program-text { background-color: #f9f9f9; border: 1px solid #ddd; padding: 15px; border-radius: 5px; line-height: 1.6; margin-bottom: 25px; }
    .objective-text textarea, .content-program-text textarea { min-height: 100px; resize: vertical; }
    .upload-section { text-align: center; padding: 20px; border: 2px dashed #ccc; border-radius: 8px; margin-top: 30px; background-color: #fafafa; }
    .upload-section input[type="file"] { margin-bottom: 15px; }
    .upload-section button, .action-buttons button {
      background-color: #28a745; color: white; padding: 10px 20px; border: none; border-radius: 5px; cursor: pointer;
      font-size: 16px; transition: background-color 0.3s ease; margin: 5px;
    }
    .upload-section button:hover, .action-buttons button:hover { background-color: #218838; }
    .action-buttons { text-align: center; margin-top: 30px; }
    .action-buttons button.btn-primary { background-color: #007bff; }
    .action-buttons button.btn-primary:hover { background-color: #0056b3; }
  </style>
</head>
<body>

<div class="franja-superior d-flex justify-content-between align-items-center px-3">
  <h2 style="color:white;" class="fw-bold text-center flex-grow-1">REGISTRO DE EVENTOS</h2>
</div>
<div class="franja-naranja"></div>

<div class="container mt-12">
  <div class="course-container">
    <h1>Datos del Curso</h1>
    <form id="courseForm">
      <div class="info-grid">
        <label for="direccion">DIRECCIÓN:</label>
        <input type="text" id="direccion" name="direccion" required>
        <label for="nombreCurso">NOMBRE DEL CURSO:</label>
        <input type="text" id="nombreCurso" name="nombreCurso" required>
        <label for="fechaInicio">FECHA INICIO:</label>
        <input type="date" id="fechaInicio" name="fechaInicio" required>
        <label for="fechaFin">FECHA FIN:</label>
        <input type="date" id="fechaFin" name="fechaFin" required>
        <!-- AÑADIDO: Campo para la Fecha de Emisión -->
        <label for="fechaEmision">FECHA DE EMISIÓN:</label>
        <input type="date" id="fechaEmision" name="fechaEmision" required>
        <!-- FIN AÑADIDO -->
        <label for="duracion">DURACIÓN:</label>
        <input type="number" id="duracion" name="duracion" required>
        <label for="modalidad">MODALIDAD:</label>
        <select id="modalidad" name="modalidad" required>
          <option value="">Seleccione una modalidad</option>
          <option value="Presencial">Presencial</option>
          <option value="Online">Online</option>
          <option value="Hibrido">Híbrido</option>
          <option value="Semipresencial">Semipresencial</option>
        </select>
        <label for="tipo">TIPO:</label>
        <select id="tipo" name="tipo" required>
          <option value="">Seleccione un tipo</option>
          <option value="Aprobacion">Aprobación</option>
          <option value="Participacion">Participación</option>
        </select>
        <label for="tipoEvento">TIPO DE EVENTO:</label>
        <select id="tipoEvento" name="tipoEvento" required>
        <option value="">Seleccione el tipo de evento</option>
        <option value="Curso">Curso</option>
        <option value="Capacitación">Capacitación</option>
        <option value="Taller">Taller</option>
        <option value="Jornada">Jornada</option>
        <option value="Conferencia">Conferencia</option>
        <option value="Simposio">Simposio</option>
        </select>
      </div>

      <div class="section-title">OBJETIVO DEL PROGRAMA</div>
      <div class="objective-text"><textarea id="objetivoPrograma" name="objetivoPrograma" required></textarea></div>

      <div class="section-title">CONTENIDO DEL PROGRAMA</div>
      <div class="content-program-text"><textarea id="contenidoPrograma" name="contenidoPrograma" required></textarea></div>

      <div class="info-grid">
        <label for="folder">FOLDER:</label>
        <input type="text" id="folder" name="folder" required>
        <label for="folio">FOLIO:</label>
        <input type="text" id="folio" name="folio" required>
        <label for="anio">AÑO:</label>
        <input type="number" id="anio" name="anio" required>
        <label for="codigo">CÓDIGO:</label>
        <input type="text" id="codigo" name="codigo" required>
      </div>

      <div class="section-title">CARGAR INFORMACIÓN DE PARTICIPANTES</div>
      <div class="upload-section">
        <input type="file" id="fileUpload" accept=".xlsx,.xls">
        <p>El documento debe contener los datos de los participantes.</p>
      </div>

      <div class="action-buttons">
        <button type="submit" class="btn-primary">Guardar Registro</button>
        <button type="reset" class="btn-secondary" style="background-color: #6c757d;">Limpiar Formulario</button>
      </div>
    </form>
  </div>
</div>

<script>
const WEBHOOK_URL = 'https://hook.us2.make.com/r2h8xbgbgddy60g7og5j2glc249ckz6g';

$(document).ready(function () {
  // AÑADIDO: Poner la fecha de hoy por defecto en el campo de emisión
  const setTodayDate = () => {
    const today = new Date();
    const yyyy = today.getFullYear();
    const mm = String(today.getMonth() + 1).padStart(2, '0'); // Enero es 0!
    const dd = String(today.getDate()).padStart(2, '0');
    const formattedToday = `${yyyy}-${mm}-${dd}`;
    $('#fechaEmision').val(formattedToday);
  };
  setTodayDate();
  // FIN AÑADIDO

  $('#modalidad').select2({ placeholder: "Seleccione una modalidad", allowClear: true });
  $('#tipo').select2({ placeholder: "Seleccione un tipo", allowClear: true });
  $('#tipoEvento').select2({ placeholder: "Seleccione el tipo de evento", allowClear: true });

  $('#courseForm').on('submit', function (event) {
    event.preventDefault();

    let formValid = true;
    // AÑADIDO: Se agrega el nuevo campo a la validación
    const requiredFields = ['#direccion', '#nombreCurso', '#fechaInicio', '#fechaFin', '#fechaEmision', '#duracion', '#modalidad', '#tipo', '#tipoEvento', '#objetivoPrograma', '#contenidoPrograma', '#folder', '#folio', '#anio', '#codigo'];
    requiredFields.forEach(field => { if (!$(field).val()) formValid = false; });

    const duracion = parseInt($('#duracion').val(), 10);
    const anio = parseInt($('#anio').val(), 10);
    if (isNaN(duracion) || duracion <= 0 || isNaN(anio)) formValid = false;

    const fechaInicio = new Date($('#fechaInicio').val());
    const fechaFin = new Date($('#fechaFin').val());
    if (fechaInicio > fechaFin) formValid = false;

    if (!formValid) {
      Swal.fire({ icon: 'error', title: 'Campos incompletos', text: 'Revise todos los datos antes de enviar.' });
      return;
    }

    const fileInput = document.getElementById('fileUpload');
    if (fileInput.files.length === 0) {
      Swal.fire({ icon: 'warning', title: 'Archivo requerido', text: 'Debe cargar el Excel de participantes.' });
      return;
    }

    const file = fileInput.files[0];
    const allowedTypes = [
      'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet',
      'application/vnd.ms-excel'
    ];
    if (!allowedTypes.includes(file.type)) {
      Swal.fire({ icon: 'error', title: 'Tipo de archivo inválido', text: 'Debe ser .xlsx o .xls' });
      return;
    }

    Swal.fire({ title: 'Enviando...', text: 'Espere un momento.', allowOutsideClick: false, didOpen: () => Swal.showLoading() });

    const reader = new FileReader();
    reader.onload = function (e) {
      const base64Data = e.target.result.split(',')[1];
      const payload = {
        direccion: $('#direccion').val(),
        nombreCurso: $('#nombreCurso').val(),
        fechaInicio: $('#fechaInicio').val(),
        fechaFin: $('#fechaFin').val(),
        fechaEmision: $('#fechaEmision').val(), // AÑADIDO: Se envía el nuevo dato
        duracion: $('#duracion').val(),
        modalidad: $('#modalidad').val(),
        tipo: $('#tipo').val(),
        tipoEvento: $('#tipoEvento').val(),
        objetivoPrograma: $('#objetivoPrograma').val(),
        contenidoPrograma: $('#contenidoPrograma').val(),
        folder: $('#folder').val(),
        folio: $('#folio').val(),
        anio: $('#anio').val(),
        codigo: $('#codigo').val(),
        archivo: {
          nombre: file.name,
          tipoMime: file.type,
          base64: base64Data
        }
      };

      $.ajax({
        url: WEBHOOK_URL,
        method: 'POST',
        contentType: 'application/json',
        data: JSON.stringify(payload),
        success: function () {
          Swal.close();
          Swal.fire({ icon: 'success', title: '¡Enviado!', text: 'Registro exitoso.' });
          $('#courseForm')[0].reset();
          $('#modalidad').val(null).trigger('change');
          $('#tipo').val(null).trigger('change');
          $('#courseStatus').text('Pendiente').removeClass('generado').addClass('pendiente');
          setTodayDate(); // AÑADIDO: Vuelve a poner la fecha de hoy después de limpiar
        },
        error: function (xhr, status, error) {
          Swal.close();
          Swal.fire({ icon: 'error', title: 'Error al enviar', text: `Error ${xhr.status}: ${xhr.responseText || error}` });
        }
      });
    };
    reader.readAsDataURL(file);
  });
});
</script>

</body>
</html>
