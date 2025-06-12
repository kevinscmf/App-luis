const casas = [
  { id: 1, ciudad: 'Bogotá', precio: 250000000, descripcion: 'Casa de 3 habitaciones con jardín.' },
  { id: 2, ciudad: 'Medellín', precio: 300000000, descripcion: 'Apartamento moderno con balcón.' },
  { id: 3, ciudad: 'Bogotá', precio: 180000000, descripcion: 'Casa pequeña en el centro.' },
];

function mostrarCasas(lista) {
  const contenedor = document.getElementById('listaCasas');
  contenedor.innerHTML = ''; // Limpiar
  lista.forEach(casa => {
    const div = document.createElement('div');
    div.className = 'casa';
    div.innerHTML = `
      <h3>${casa.ciudad}</h3>
      <p>${casa.descripcion}</p>
      <p><strong>Precio:</strong> $${casa.precio.toLocaleString()}</p>
      <button onclick="contactar(${casa.id})">Contactar</button>
    `;
    contenedor.appendChild(div);
  });
}

function filtrarCasas() {
  const ciudad = document.getElementById('filtroCiudad').value;
  if (ciudad === 'todas') {
    mostrarCasas(casas);
  } else {
    const filtradas = casas.filter(casa => casa.ciudad === ciudad);
    mostrarCasas(filtradas);
  }
}

function contactar(id) {
  const casa = casas.find(c => c.id === id);
  alert(`Gracias por tu interés en la casa de ${casa.ciudad}. Un agente te contactará pronto.`);
}

// Mostrar todas al inicio
mostrarCasas(casas);
