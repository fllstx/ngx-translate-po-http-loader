# ngx-translate-po-http-loader

Load po files for use with `ngx-translate`

## Installation

```sh
npm i @ngx-translate/core --save
npm i @fullstax/ngx-translate-po-http-loader --save
```

## Usage

```ts
import { HttpClient, HttpClientModule } from '@angular/common/http';

import { TranslateModule, TranslateLoader } from '@ngx-translate/core';
import { TranslatePoHttpLoader } from '@fullstax/ngx-translate-po-http-loader';

export function createTranslateLoader(http: HttpClient) {
  return new TranslatePoHttpLoader(http, 'assets/i18n', '.po');
}
// or
export function createTranslateLoader(http: HttpClient) {
  return new MultiTranslatePoHttpLoader(http, [
    { prefix: 'assets/i18n', suffix: '.po' },
    { prefix: 'assets/i18n/lib1', suffix: '.po' }
  ]);
}
@NgModule({
  imports: [
    BrowserModule,
    HttpClientModule,
    TranslateModule.forRoot({
      loader: {
        provide: TranslateLoader,
        useFactory: createTranslateLoader,
        deps: [HttpClient]
      }
    })
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

## License

This package is based on [biesbjerg/ngx-translate-po-http-loader](https://github.com/biesbjerg/ngx-translate-po-http-loader/commit/7d39be13ff5192cf5d2018a2d3e2272973abcd15) and includes useful commits from the following forks:

* [talkspiritlab/ngx-translate-po-http-loader](https://github.com/talkspiritlab/ngx-translate-po-http-loader/tree/bcf3a2491942f2a441d58b4986b6855fd5eec090)
* [daniel-schulz/ngx-translate-po-http-loader](https://github.com/daniel-schulz/ngx-translate-po-http-loader/commit/62ae7d3859286a3f97d2e6b1a473de73c643d499)
* [sergiojoker11/ngx-translate-po-http-loader](https://github.com/sergiojoker11/ngx-translate-po-http-loader/commit/d680750e91843fe49ee9c4def6bafaa42cdc45ac)
