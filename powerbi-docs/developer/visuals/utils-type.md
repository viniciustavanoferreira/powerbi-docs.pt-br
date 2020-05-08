---
title: Introdução ao uso de utilitários de tipo no visual do Power BI
description: Este artigo descreve como usar os utilitários SVG para estender os tipos básicos para visuais do Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 5a3cfb7ea9c9f398193b45652aa43c6b83c8f70b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377985"
---
# <a name="type-utils"></a>Utilitários de tipo

TypeUtils é um conjunto de funções e classes para estender os tipos básicos para visuais de Power BI.

## <a name="installation"></a>Instalação

Para instalar o pacote, você deve executar o seguinte comando no diretório com seu visual personalizado atual:

npm install powerbi-visuals-utils-typeutils --save Esse comando instala o pacote e adiciona um pacote como uma dependência ao package.json

## <a name="double"></a>Double

O `Double` fornece capacidades de manipulação da precisão dos números.

O módulo fornece as seguintes funções:

### <a name="pow10"></a>pow10

Essa função retorna a potência de 10 do número.

```typescript
function pow10(exp: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Essa função retorna um logaritmo de base 10 do número.

```typescript
function log10(val: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Essa função retorna uma potência de 10 que representa a precisão do número.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Essa função verifica se um delta entre dois números é menor que a precisão fornecida.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Essa função verifica se o primeiro valor é menor que o segundo valor.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Essa função verifica se o primeiro valor é menor ou igual ao segundo.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Essa função verifica se o primeiro valor é maior que o segundo.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Essa função verifica se o primeiro valor é maior ou igual ao segundo.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Essa função arredonda o número para baixo, com a precisão fornecida.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Essa função `ceils` o número com a precisão fornecida.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Essa função arredonda o número para baixo, até alcançar a precisão fornecida.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Essa função `ceils` o número até a precisão fornecida.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Essa função arredonda o número, até alcançar a precisão fornecida.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Essa função retorna um número entre o mín. e o máx.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Essa função arredonda o número.

```typescript
function round(x: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Essa função remove o ruído decimal.

```typescript
function removeDecimalNoise(value: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Essa função verifica se o número é inteiro.

```typescript
function isInteger(value: number): boolean;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Essa função incrementa o primeiro número pelo segundo número fornecido e retorna o primeiro número arredondado.

```typescript
function toIncrement(value: number, increment: number): number;
```

Exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Protótipo

O `Prototype` fornece habilidades para herdar objetos.

O módulo fornece as seguintes funções:

## <a name="inherit"></a>inherit

Essa função retorna um novo objeto, que tem o objeto fornecido como seu próprio protótipo.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Exemplo:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Essa função retornará um novo objeto que tem o objeto fornecido como seu próprio protótipo se, e somente se, o protótipo não tiver sido definido.

```typescript
function inheritSingle<T>(obj: T): T;
```

Exemplo:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

O `PixelConverter` fornece uma capacidade de converter pixels em pontos e pontos em pixels.

O módulo fornece as seguintes funções:

## <a name="tostring"></a>toString

Essa função converte o valor de pixel em uma cadeia de caracteres.

```typescript
function toString(px: number): string;
```

Exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Essa função converte o valor de ponto fornecido para o valor de pixel e retorna a interpretação da cadeia de caracteres.

```typescript
function fromPoint(pt: number): string;
```

Exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Essa função converte o valor de ponto fornecido para o valor de pixel.

```typescript
function fromPointToPixel(pt: number): number;
```

Exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Essa função converte o valor de pixel para o valor de ponto.

```typescript
function toPoint(px: number): number;
```

Exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
