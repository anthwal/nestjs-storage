<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>

<p align="center">
    nestjs-storage is manage file Storage wrapping package flydrive
</p>
<p align="center">
    <a href="https://www.npmjs.com/org/anthwal"><img src="https://img.shields.io/npm/v/@anthwal/nestjs-storage.svg" alt="NPM Version" /></a>
    <a href="https://www.npmjs.com/org/anthwal"><img src="https://img.shields.io/npm/l/@anthwal/nestjs-storage.svg" alt="Package License" /></a>
    <a href="https://www.npmjs.com/org/anthwal"><img src="https://img.shields.io/npm/dm/@anthwal/nestjs-storage.svg" alt="NPM Downloads" /></a>
</p>

## Installation

```bash
$ npm i --save @anthwal/nestjs-storage @slynova/flydrive

# optional with s3 driver
$ npm i --save @slynova/flydrive-s3

# optional with gcs driver
$ npm i --save @slynova/flydrive-gcs
```

## Example

```typescript
// app.module.ts
import { Module } from '@nestjs/common'
import { StorageModule, DriverType, StorageService } from '@anthwal/nestjs-storage';

@Module({
  imports: [
    StorageModule.forRoot({
      default: 'local',
      disks: {
        local: {
          driver: DriverType.LOCAL,
          config: {
            root: process.cwd(),
          },
        },
      },
    }),
  ],
})
export class AppModule {
  constructor(private storage: StorageService) {
    this.storage.getDisk().put('test.txt', 'text content');
  }
}
```

## Support

nestjs-storage is an MIT-licensed open source project. If this library is helpful, please click star to support it.

## Stay in touch

- Author - [Arun Anthwal](https://github.com/anthwal)

## License

nestjs-storage is MIT licensed.
