# Rinc-n-Tanguero-Interactivo
El objetivo es ser un portal cultural digital donde el usuario no solo presiona "Play", sino que también aprende sobre la historia, la literatura y el movimiento que definen al tango.El propósito 1. Difusión y Disfrute Musical   2. Enriquecimiento Cultural Interactivo.
<iframe src="https://claude.site/public/artifacts/7f431ec9-4d51-4394-a5ea-ba36bebbba3a/embed" title="Claude Artifact" width="100%" height="600" frameborder="0" allow="clipboard-write" allowfullscreen></iframe>
import React, { useState } from 'react';
import { Music, Info, Footprints, Youtube, Sparkles, Volume2, Search } from 'lucide-react';

const tangos = [
  {
    titulo: "La Cumparsita",
    compositor: "Gerardo Matos Rodríguez",
    año: 1916,
    orquestaAudio: "Juan D'Arienzo",
    curiosidades: [
      "Es el tango más famoso del mundo y fue declarado himno cultural de Uruguay en 1998",
      "Fue compuesto por Matos Rodríguez cuando tenía entre 17 y 20 años",
      "Originalmente fue una marcha para el carnaval de la Federación de Estudiantes",
      "Roberto Firpo agregó partes de sus tangos al arreglo original",
      "Matos Rodríguez pasó 20 años en juicios para recuperar los derechos"
    ],
    historia: "Compuesta en 1916 en Montevideo, nació como una marcha carnavalera. Fue estrenada por Roberto Firpo en el café La Giralda el 19 de abril de 1917.",
    pasos: ["Caminata básica en 8 tiempos", "Ocho adelante y atrás", "Giro completo", "Resolución con sacada"]
  },
  {
    titulo: "El Día Que Me Quieras",
    compositor: "Carlos Gardel y Alfredo Le Pera",
    año: 1935,
    orquestaAudio: "Carlos Gardel",
    curiosidades: [
      "Fue filmada en enero de 1935 en los estudios Paramount de Nueva York",
      "Se estrenó el 5 de julio de 1935 en La Habana, días después de la muerte de Gardel",
      "El joven Astor Piazzolla de 12 años apareció como canillita en esta película",
      "Gardel le escribió a su representante que era su mejor trabajo cinematográfico",
      "La película fue restaurada en 4K por la Cinemateca Argentina en 2016"
    ],
    historia: "La última película de Gardel filmada en Nueva York. El encuentro entre Gardel y el niño Piazzolla durante el rodaje fue histórico.",
    pasos: ["Caminata elegante", "Ocho romántico", "Giro suave", "Finalización emotiva"]
  },
  {
    titulo: "Por Una Cabeza",
    compositor: "Carlos Gardel y Alfredo Le Pera",
    año: 1935,
    orquestaAudio: "Carlos Gardel",
    curiosidades: [
      "Compuesta en Nueva York para la película 'Tango Bar'",
      "'Por una cabeza' es jerga hípica: cuando un caballo gana por muy poco",
      "Ha aparecido en más de 30 películas incluyendo 'Perfume de Mujer'",
      "Gardel perdió una apuesta inspirando el tema",
      "Gardel murió 3 meses después en Medellín"
    ],
    historia: "La letra compara la adicción al juego de caballos con el amor apasionado y destructivo.",
    pasos: ["Abrazo cerrado", "Ocho cortado", "Parada dramática", "Giro con adorno"]
  },
  {
    titulo: "Mi Buenos Aires Querido",
    compositor: "Carlos Gardel y Alfredo Le Pera",
    año: 1934,
    orquestaAudio: "Carlos Gardel",
    curiosidades: [
      "Compuesto para la película 'Cuesta abajo' de 1934",
      "Es uno de los tangos más populares de Gardel",
      "Se convirtió en himno no oficial de Buenos Aires",
      "Ha sido versionado en múltiples idiomas",
      "Símbolo de la ciudad porteña"
    ],
    historia: "Una oda nostálgica a Buenos Aires evocando los recuerdos de la ciudad querida.",
    pasos: ["Caminata orgullosa", "Ocho nostálgico", "Giro completo", "Pose característica"]
  },
  {
    titulo: "Volver",
    compositor: "Carlos Gardel y Alfredo Le Pera",
    año: 1934,
    orquestaAudio: "Carlos Gardel",
    curiosidades: [
      "Grabada para la película 'El día que me quieras' en 1935",
      "La frase 'que veinte años no es nada' es emblemática",
      "Una de las últimas composiciones antes de su muerte",
      "Pedro Almodóvar tituló su película inspirado en este tango",
      "Es de los tangos más versionados internacionalmente"
    ],
    historia: "Trata sobre el regreso al lugar de origen tras una larga ausencia.",
    pasos: ["Caminata melancólica", "Ocho nostálgico", "Medio giro", "Resolución emotiva"]
  },
  {
    titulo: "Cuesta Abajo",
    compositor: "Carlos Gardel y Alfredo Le Pera",
    año: 1934,
    orquestaAudio: "Carlos Gardel",
    curiosidades: [
      "Compuesto durante el rodaje de la película homónima en 1934",
      "Grabado el 30 de julio de 1934 en Nueva York",
      "La película se estrenó el 10 de agosto de 1934",
      "Es también considerado un 'Volver' por su temática",
      "Contiene versos antológicos sobre el dolor del amor"
    ],
    historia: "Habla de un protagonista en decadencia que evoca el pasado que añora.",
    pasos: ["Caminata con peso", "Ocho dramático", "Pausa emotiva", "Resolución contenida"]
  },
  {
    titulo: "Adiós Nonino",
    compositor: "Astor Piazzolla",
    año: 1959,
    orquestaAudio: "Astor Piazzolla",
    curiosidades: [
      "Compuesta tras la muerte de su padre Vicente",
      "Estaba de gira en Puerto Rico cuando recibió la noticia",
      "Piazzolla dijo: 'Es el tema más lindo que escribí'",
      "Se basó en un tango anterior llamado 'Nonino'",
      "Es su obra cumbre del tango nuevo"
    ],
    historia: "Devastado por la muerte de su padre, Piazzolla compuso esta obra maestra en Nueva York.",
    pasos: ["Caminata melancólica", "Volcada con suspensión", "Barrida circular", "Gancho emotivo"]
  },
  {
    titulo: "Libertango",
    compositor: "Astor Piazzolla",
    año: 1974,
    orquestaAudio: "Astor Piazzolla",
    curiosidades: [
      "El nombre une 'Libertad' y 'Tango'",
      "Compuesto cuando Piazzolla vivía en Italia",
      "Popularizó el 'tango nuevo' a nivel mundial",
      "Ha sido versionado por artistas de jazz",
      "Una de las composiciones más reconocidas de Piazzolla"
    ],
    historia: "Marca la consolidación del tango nuevo fusionando tango con jazz y música clásica.",
    pasos: ["Entrada moderna", "Caminata marcada", "Giros dinámicos", "Movimientos innovadores"]
  },
  {
    titulo: "El Choclo",
    compositor: "Ángel Villoldo",
    año: 1903,
    orquestaAudio: "Juan D'Arienzo",
    curiosidades: [
      "Uno de los tangos más antiguos que se conservan",
      "Villoldo era 'El Padre del Tango'",
      "'Choclo' significa 'mazorca de maíz' en lunfardo",
      "Utilizado en Los Simpson",
      "Representa la época dorada del tango"
    ],
    historia: "Compuesto en 1903 cuando el tango se bailaba en los suburbios.",
    pasos: ["Salida en cruz", "Ocho con enrosque", "Barrida lineal", "Gancho mutuo"]
  },
  {
    titulo: "La Yumba",
    compositor: "Osvaldo Pugliese",
    año: 1946,
    orquestaAudio: "Osvaldo Pugliese",
    curiosidades: [
      "El ritmo definió el sonido de la Orquesta Pugliese",
      "'La yumba' significa 'fiesta' o 'trabajo' en lunfardo",
      "Uno de los tangos instrumentales más bailables",
      "El marcato del piano es su sello",
      "Se convirtió en himno de las milongas"
    ],
    historia: "Revolucionó el tango bailable en 1946 con su ritmo marcado.",
    pasos: ["Caminata firme", "Ochos con energía", "Giros con impulso", "Sacadas contundentes"]
  },
  {
    titulo: "Caminito",
    compositor: "Juan de Dios Filiberto y Gabino Coria Peñaloza",
    año: 1926,
    orquestaAudio: "Francisco Canaro",
    curiosidades: [
      "Tango emblemático del barrio La Boca",
      "La calle turística 'Caminito' lleva su nombre",
      "La letra fue inspirada en un sendero de Tucumán",
      "Se convirtió en símbolo del tango para turistas",
      "Une la nostalgia provinciana con el espíritu porteño"
    ],
    historia: "La letra habla de un camino que ya no existe, lleno de recuerdos del pasado.",
    pasos: ["Caminata nostálgica", "Ocho con sentimiento", "Giro suave", "Abrazo cerrado"]
  },
  {
    titulo: "Nostalgias",
    compositor: "Juan Carlos Cobián y Enrique Cadícamo",
    año: 1936,
    orquestaAudio: "Aníbal Troilo",
    curiosidades: [
      "Rechazado originalmente por 'antipopular'",
      "Escrita para una obra sobre Gardel",
      "Charlo lo cantó en Radio Belgrano",
      "Se convirtió en éxito inmediato",
      "Fue editado en París, Londres y Nueva York"
    ],
    historia: "Expresa el dolor de un amor perdido y el deseo de olvidar.",
    pasos: ["Abrazo melancólico", "Caminata dramática", "Ocho cortado", "Giro nostálgico"]
  },
  {
    titulo: "Malena",
    compositor: "Lucio Demare y Homero Manzi",
    año: 1941,
    orquestaAudio: "Aníbal Troilo",
    curiosidades: [
      "Malena es un personaje ficticio",
      "Homero Manzi fue uno de los letristas más importantes",
      "Representa la melancolía del tango porteño",
      "Símbolo del tango-canción de los años 40",
      "Interpretada por los más grandes cantantes"
    ],
    historia: "Malena personifica el espíritu del tango con todo el dolor y la pasión.",
    pasos: ["Abrazo íntimo", "Caminata expresiva", "Medio giro con sentada", "Resolución emotiva"]
  },
  {
    titulo: "Uno",
    compositor: "Mariano Mores y Enrique Santos Discépolo",
    año: 1943,
    orquestaAudio: "Osvaldo Pugliese",
    curiosidades: [
      "Discépolo tardó 3 años en escribir la letra",
      "Nació durante una profunda crisis personal",
      "El título original era 'Si yo tuviera un corazón'",
      "Estrenado por Tania en el Teatro Astral",
      "Es uno de los 'tangos fundamentales'"
    ],
    historia: "Trata sobre la desilusión de quien ya no puede amar después de tanto sufrimiento.",
    pasos: ["Caminata lenta", "Ocho introspectivo", "Parada dramática", "Abrazo contenido"]
  },
  {
    titulo: "Balada Para Un Loco",
    compositor: "Astor Piazzolla y Horacio Ferrer",
    año: 1969,
    orquestaAudio: "Astor Piazzolla",
    curiosidades: [
      "Interpretada por primera vez por Amelita Baltar",
      "Causó escándalo al mezclar tango con rock",
      "La letra habla de un amor surrealista",
      "Parte de la dupla Piazzolla-Ferrer",
      "Revolucionó el tango"
    ],
    historia: "Cuenta la historia de un hombre que invita a una mujer a volar sobre Buenos Aires.",
    pasos: ["Caminar enérgico", "Giro rápido", "Volcada expresiva", "Gancho alto"]
  },
  {
    titulo: "Sentimental",
    compositor: "Carlos Gardel y Alfredo Le Pera",
    año: 1932,
    orquestaAudio: "Carlos Gardel",
    curiosidades: [
      "Título representativo del tono nostálgico de Gardel",
      "Grabado en los años dorados de su carrera",
      "Refleja el sentimentalismo del tango-canción",
      "Popular en las milongas de los años 30",
      "Parte del repertorio clásico gardeliano"
    ],
    historia: "Captura la esencia sentimental que caracterizó la dupla Gardel-Le Pera.",
    pasos: ["Caminata suave", "Ocho con emoción", "Giro delicado", "Abrazo nostálgico"]
  },
  {
    titulo: "Milonga de la Tarde",
    compositor: "Aníbal Troilo y Homero Manzi",
    año: 1945,
    orquestaAudio: "Aníbal Troilo",
    curiosidades: [
      "Ritmo suave ideal para baile de tarde",
      "Troilo llevó la orquesta a un sonido íntimo",
      "Popular en las milongas vespertinas",
      "Combina melancolía con ritmo bailable",
      "Parte del repertorio clásico de Troilo"
    ],
    historia: "Evoca las tardes en Buenos Aires con ese ritmo que invita al baile tranquilo.",
    pasos: ["Paso de milonga básico", "Traspié", "Giro simple", "Contragiro"]
  },
  {
    titulo: "Olas de Tango",
    compositor: "Francisco Canaro y José Padilla",
    año: 1931,
    orquestaAudio: "Francisco Canaro",
    curiosidades: [
      "Arreglo que recuerda el sonido de la orilla",
      "Canaro fue uno de los pioneros del tango",
      "Evoca el Río de la Plata",
      "Popular entre los habitantes del puerto",
      "Ritmo ondulante como las olas"
    ],
    historia: "Evoca el movimiento de las olas del Río de la Plata.",
    pasos: ["Caminata ondulante", "Ocho fluido", "Giro como ola", "Resolución suave"]
  },
  {
    titulo: "Noches de La Boca",
    compositor: "Juan de Dios Filiberto y Pepita D'Amalfi",
    año: 1927,
    orquestaAudio: "Francisco Canaro",
    curiosidades: [
      "Estilo clásico de La Boca",
      "Evoca el barrio portuario más famoso",
      "Popular entre los inmigrantes italianos",
      "Refleja la vida nocturna del barrio",
      "Patrimonio cultural de Buenos Aires"
    ],
    historia: "Captura las noches del emblemático barrio de La Boca.",
    pasos: ["Caminata del barrio", "Ocho italiano", "Giro de conventillo", "Abrazo portuario"]
  },
  {
    titulo: "Río de Luces",
    compositor: "Astor Piazzolla y Horacio Ferrer",
    año: 1981,
    orquestaAudio: "Astor Piazzolla",
    curiosidades: [
      "Sonoridad de cuerdas y viento en diálogo",
      "Evoca el Río de la Plata iluminado",
      "Arreglo complejo y sofisticado",
      "Popular en conciertos de Piazzolla",
      "Muestra la madurez compositiva"
    ],
    historia: "Imagina el Río de la Plata iluminado por las luces de la ciudad.",
    pasos: ["Caminata luminosa", "Ocho brillante", "Giro reflejo", "Finalización en luz"]
  }
];

export default function RinconTanguero() {
  const [tangoActual, setTangoActual] = useState(null);
  const [seccionActiva, setSeccionActiva] = useState('curiosidades');
  const [busqueda, setBusqueda] = useState('');
  const [mostrarLista, setMostrarLista] = useState(false);

  const sugerirTango = () => {
    const indiceAleatorio = Math.floor(Math.random() * tangos.length);
    setTangoActual(tangos[indiceAleatorio]);
    setSeccionActiva('curiosidades');
    setMostrarLista(false);
  };

  const tangosFiltrados = tangos.filter(tango =>
    tango.titulo.toLowerCase().includes(busqueda.toLowerCase()) ||
    tango.compositor.toLowerCase().includes(busqueda.toLowerCase())
  );

  const seleccionarTango = (tango) => {
    setTangoActual(tango);
    setSeccionActiva('curiosidades');
    setMostrarLista(false);
    setBusqueda('');
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-red-900 via-red-800 to-black text-white p-4 md:p-8">
      <div className="max-w-4xl mx-auto">
        <div className="text-center mb-8">
          <h1 className="text-4xl md:text-5xl font-bold mb-2 text-yellow-400">🎵 Rincón Tanguero 🎵</h1>
          <p className="text-lg md:text-xl text-red-200">Descubre la magia del tango argentino</p>
          <p className="text-sm text-yellow-300 mt-2">📚 {tangos.length} tangos disponibles</p>
        </div>

        <div className="mb-6 bg-black bg-opacity-50 rounded-lg p-4 border border-yellow-500">
          <div className="flex items-center gap-2 mb-2">
            <Search className="text-yellow-400" size={20} />
            <span className="font-semibold">Buscar Tango</span>
          </div>
          <input
            type="text"
            placeholder="Busca por título o compositor..."
            value={busqueda}
            onChange={(e) => {
              setBusqueda(e.target.value);
              setMostrarLista(e.target.value.length > 0);
            }}
            className="w-full p-3 rounded bg-red-950 text-white border border-yellow-500 focus:outline-none focus:border-yellow-400"
          />
          
          {mostrarLista && tangosFiltrados.length > 0 && (
            <div className="mt-2 max-h-60 overflow-y-auto bg-red-950 rounded border border-yellow-500">
              {tangosFiltrados.map((tango, index) => (
                <div
                  key={index}
                  onClick={() => seleccionarTango(tango)}
                  className="p-3 hover:bg-red-900 cursor-pointer border-b border-red-800 last:border-b-0"
                >
                  <p className="font-semibold text-yellow-300">{tango.titulo}</p>
                  <p className="text-sm text-red-200">{tango.compositor} ({tango.año})</p>
                </div>
              ))}
            </div>
          )}
        </div>

        <div className="text-center mb-8">
          <button
            onClick={sugerirTango}
            className="bg-yellow-500 hover:bg-yellow-600 text-black font-bold py-4 px-6 md:px-8 rounded-full text-lg md:text-xl transition-all transform hover:scale-105 shadow-lg flex items-center gap-3 mx-auto"
          >
            <Sparkles size={28} />
            Sugerir Tango Aleatorio
          </button>
        </div>

        {tangoActual && (
          <div className="bg-black bg-opacity-50 rounded-lg p-4 md:p-6 shadow-2xl border-2 border-yellow-500">
            <div className="text-center mb-6">
              <h2 className="text-3xl md:text-4xl font-bold text-yellow-400 mb-2">{tangoActual.titulo}</h2>
              <p className="text-lg md:text-xl text-red-200">
                <Music className="inline mr-2" size={20} />
                {tangoActual.compositor} ({tangoActual.año})
              </p>
            </div>

            <div className="mb-6 bg-gradient-to-r from-red-950 to-red-900 rounded-lg p-4 border border-yellow-500">
              <div className="flex items-center gap-2 mb-3">
                <Volume2 className="text-yellow-400" size={24} />
                <span className="font-semibold text-lg">Escuchar Música de Tango</span>
              </div>
              <div className="bg-black bg-opacity-40 rounded p-3 mb-3">
                <p className="text-sm text-yellow-200 mb-2">
                  🎺 Orquesta: <span className="font-bold text-yellow-400">{tangoActual.orquestaAudio}</span>
                </p>
                <p className="text-xs text-red-200">
                  Audio de las grandes orquestas típicas argentinas
                </p>
              </div>
              <a 
                href={`https://www.youtube.com/results?search_query=${encodeURIComponent(tangoActual.titulo + ' ' + tangoActual.orquestaAudio + ' tango')}`}
                target="_blank" 
                rel="noopener noreferrer"
                className="bg-yellow-500 hover:bg-yellow-600 text-black font-bold py-3 px-6 rounded-lg inline-flex items-center gap-2 transition-all w-full md:w-auto justify-center"
              >
                <Youtube size={20} />
                Buscar en YouTube
              </a>
            </div>

            <div className="flex gap-2 mb-6 flex-wrap">
              <button
                onClick={() => setSeccionActiva('curiosidades')}
                className={`flex items-center gap-2 px-3 md:px-4 py-2 rounded-lg font-semibold transition-all text-sm md:text-base ${
                  seccionActiva === 'curiosidades' ? 'bg-yellow-500 text-black' : 'bg-red-950 text-white hover:bg-red-900'
                }`}
              >
                <Sparkles size={18} />
                Curiosidades
              </button>
              <button
                onClick={() => setSeccionActiva('historia')}
                className={`flex items-center gap-2 px-3 md:px-4 py-2 rounded-lg font-semibold transition-all text-sm md:text-base ${
                  seccionActiva === 'historia' ? 'bg-yellow-500 text-black' : 'bg-red-950 text-white hover:bg-red-900'
                }`}
              >
                <Info size={18} />
                Historia
              </button>
              <button
                onClick={() => setSeccionActiva('pasos')}
                className={`flex items-center gap-2 px-3 md:px-4 py-2 rounded-lg font-semibold transition-all text-sm md:text-base ${
                  seccionActiva === 'pasos' ? 'bg-yellow-500 text-black' : 'bg-red-950 text-white hover:bg-red-900'
                }`}
              >
                <Footprints size={18} />
                Pasos
              </button>
            </div>

            <div className="bg-red-950 bg-opacity-70 rounded-lg p-4 md:p-6">
              {seccionActiva === 'curiosidades' && (
                <div>
                  <h3 className="text-xl md:text-2xl font-bold text-yellow-400 mb-4 flex items-center gap-2">
                    <Sparkles size={24} />
                    Datos Curiosos
                  </h3>
                  <ul className="space-y-3">
                    {tangoActual.curiosidades.map((curiosidad, index) => (
                      <li key={index} className="flex items-start gap-3 text-base md:text-lg">
                        <span className="text-yellow-400 text-2xl">•</span>
                        <span>{curiosidad}</span>
                      </li>
                    ))}
                  </ul>
                </div>
              )}

              {seccionActiva === 'historia' && (
                <div>
                  <h3 className="text-xl md:text-2xl font-bold text-yellow-400 mb-4 flex items-center gap-2">
                    <Info size={24} />
                    Historia
                  </h3>
                  <p className="text-base md:text-lg leading-relaxed">{tangoActual.historia}</p>
                </div>
              )}

              {seccionActiva === 'pasos' && (
                <div>
                  <h3 className="text-xl md:text-2xl font-bold text-yellow-400 mb-4 flex items-center gap-2">
                    <Footprints size={24} />
                    Pasos Sugeridos
                  </h3>
                  <div className="space-y-4">
                    {tangoActual.pasos.map((paso, index) => (
                      <div key={index} className="bg-black bg-opacity-40 p-4 rounded-lg">
                        <div className="flex items-center gap-3">
                          <div className="bg-yellow-500 text-black font-bold rounded-full w-8 h-8 flex items-center justify-center flex-shrink-0">
                            {index + 1}
                          </div>
                          <span className="text-base md:text-lg">{paso}</span>
                        </div>
                      </div>
                    ))}
                  </div>
                  <p className="text-red-200 mt-4 italic text-center text-sm md:text-base">
                    💃 Practica con paciencia y disfruta cada paso 🕺
                  </p>
                </div>
              )}
            </div>
          </div>
        )}

        {!tangoActual && (
          <div className="text-center text-yellow-200 text-lg md:text-xl mt-12">
            <p className="mb-4">¡Bienvenido al mundo del tango!</p>
            <p className="px-4">Haz clic en el botón para descubrir un tango y comenzar tu aprendizaje</p>
            <div className="text-5xl md:text-6xl mt-6">🎭</div>
          </div>
        )}
      </div>
    </div>
  );
}
