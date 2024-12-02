<template>
    <div class="container mt-5">
      <!-- Container para o título -->
      <div class="title-container text-center py-3">
        <h1>Tradutor de Braille</h1>
      </div>
  
      <div class="form-group mb-4">
        <label for="textoInput">Digite o texto:</label>
        <textarea
          id="textoInput"
          v-model="texto"
          class="form-control"
          rows="4"
          placeholder="Digite seu texto aqui"
        ></textarea>
      </div>
  
      <button @click="traduzir" class="btn btn-preto btn-block mb-4">Traduzir</button>
  
      <div class="form-group">
        <label for="resultadoOutput">Resultado em Braille:</label>
        <textarea
          id="resultadoOutput"
          class="form-control"
          rows="4"
          :value="resultado"
          readonly
        ></textarea>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        texto: '',
        resultado: '',
        brailleMap: {
          a: '⠁', b: '⠃', c: '⠉', d: '⠙', e: '⠑',
          f: '⠋', g: '⠛', h: '⠓', i: '⠊', j: '⠚',
          k: '⠅', l: '⠇', m: '⠍', n: '⠝', o: '⠕',
          p: '⠏', q: '⠟', r: '⠗', s: '⠎', t: '⠞',
          u: '⠥', v: '⠧', w: '⠺', x: '⠭', y: '⠽', z: '⠵',
  
          á: '⠷', é: '⠿', í: '⠽', ó: '⠬', ú: '⠾',
  
          à: '⠢',
  
          ê: '⠮', ô: '⠹',
  
          ã: '⠜', õ: '⠪',
  
          ç: '⠆',
  
          '1': '⠼⠁', '2': '⠼⠃', '3': '⠼⠉', '4': '⠼⠙', '5': '⠼⠑',
          '6': '⠼⠋', '7': '⠼⠛', '8': '⠼⠓', '9': '⠼⠊', '0': '⠼⠚',
  
          '.': '⠲', ',': '⠂', '?': '⠦', '!': '⠖', ':': '⠱',
          ';': '⠆', '"': '⠶', '(': '⠶⠣', ')': '⠶⠜', '-': '⠤',
          '/': '⠸⠌', '@': '⠈⠁', '#': '⠼⠓', '&': '⠠', '+': '⠖',
          '=': '⠶⠤', ' ': ' ',
  
          '*': '⠐', '%': '⠨⠴',
        },
      };
    },
    methods: {
      traduzir() {
        this.resultado = this.texto
          .toLowerCase()
          .split('')
          .map(letra => this.brailleMap[letra] || '?')
          .join('');
      },
    },
  };
  </script>
  
  <style>
  .container {
    max-width: 600px;
    margin: 0 auto;
  }
  
  textarea {
    font-size: 1rem;
    resize: none;
  }
  
  .title-container {
    background-color: #000;
    color: white;
    border-radius: 5px;
    margin-bottom: 20px;
  }
  
  .btn-preto {
  background-color: #000 !important;
  color: white !important;
  border: none !important;
}

.btn-preto:hover {
  background-color: #333 !important;
}
  </style>
  