# Angular PDF Viewer

<p align="center">
  <a href="https://www.npmjs.com/package/ng2-pdf-viewer">
    <img src="https://img.shields.io/npm/dm/ng2-pdf-viewer.svg?style=flat" alt="downloads">
  </a>
  <a href="https://badge.fury.io/js/ng2-pdf-viewer">
    <img src="https://badge.fury.io/js/ng2-pdf-viewer.svg" alt="npm version">
  </a>
  <a href="https://gitter.im/ngx-pdf-viewer/Lobby" title="Gitter">
    <img src="https://img.shields.io/gitter/room/nwjs/nw.js.svg" alt="Gitter"/>
  </a>
  <a href="https://www.paypal.me/vadimdez" title="Donate to this project using Paypal">
    <img src="https://img.shields.io/badge/paypal-donate-yellow.svg" alt="PayPal donate button" />
  </a>
</p>

> PDF Viewer Component for Angular 5+

## 📦 Instalação

### Angular >= 12

```bash
npm install ng2-pdf-viewer
```


import { PdfViewerModule } from 'ng2-pdf-viewer';

@NgModule({
  imports: [PdfViewerModule],
})
export class AppModule {}

<pdf-viewer [src]="pdfSrc" [render-text]="true" [original-size]="false" style="width: 400px; height: 500px">
</pdf-viewer>

pdfSrc = 'https://vadimdez.github.io/ng2-pdf-viewer/assets/pdf-test.pdf';

### ⚠️ Atualização necessária para pdfjs-dist

Este projeto usa internamente o PDFPageViewBuffer, que a partir de versões recentes do pdfjs-dist utiliza o tipo SetIterator, que não é aceito como valor em ambientes TypeScript modernos (ex: Angular 16+).
Para evitar o erro:

TS2693: 'SetIterator' only refers to a type, but is being used as a value here.

Siga os passos abaixo.

##Localize o arquivo onde a classe PDFPageViewBuffer é declarada, normalmente em:

```bash
node_modules/pdfjs-dist/web/pdf_viewer.js
```
Altere o seguinte trecho:

```bash
[Symbol.iterator](): SetIterator<any>;
```

Para:

```bash
[Symbol.iterator](): Iterator<any>;
```
Essa mudança garante compatibilidade com o TypeScript e browsers modernos.
