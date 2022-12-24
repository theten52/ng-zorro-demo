# NgZorroDemo

这个项目是一个 ng-zorro-antd 的demo。重点是官方文档中使用的命令执行后出现的问题的解决。

官方文档地址： https://ng.ant.design/docs/schematics/zh

使用的版本信息为：
```

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/
    

Angular CLI: 12.2.18
Node: 12.22.7
Package Manager: npm 6.14.15
OS: darwin x64

Angular: 12.2.17
... animations, common, compiler, compiler-cli, core, forms
... platform-browser, platform-browser-dynamic, router

Package                         Version
---------------------------------------------------------
@angular-devkit/architect       0.1202.18 (cli-only)
@angular-devkit/build-angular   12.2.18
@angular-devkit/core            12.2.18 (cli-only)
@angular-devkit/schematics      12.2.18 (cli-only)
@angular/cli                    12.2.18
@schematics/angular             12.2.18 (cli-only)
rxjs                            6.6.7
typescript                      4.3.5
```
# 相关问题：
# 1. NG8002: Can't bind to 'formGroup' since it isn't a known property of 'form'.
在src/app/app.module.ts中导入ReactiveFormsModule
```
import { FormsModule, ReactiveFormsModule } from '@angular/forms';
...

registerLocaleData(en);

@NgModule({
  declarations: [
    AppComponent,
    LoginComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
    ReactiveFormsModule,
    ...
```
# 2. error NG8001: 'nz-form-item' is not a known element:
```text
Error: src/app/login/login.component.html:3:7 - error NG8001: 'nz-form-item' is not a known element:
1. If 'nz-form-item' is an Angular component, then verify that it is part of this module.
2. If 'nz-form-item' is a Web Component then add 'CUSTOM_ELEMENTS_SCHEMA' to the '@NgModule.schemas' of this component to suppress this message.
```
 ## 解决方式：
 1. 在app.module.ts中导入并导出nz相关组件：
 ```
 import { NzButtonModule } from 'ng-zorro-antd/button';
import { NzDividerModule } from 'ng-zorro-antd/divider';
import { NzFormModule } from 'ng-zorro-antd/form';
import { NzInputModule } from 'ng-zorro-antd/input';
import { NzMenuModule } from 'ng-zorro-antd/menu';
import { NzMessageModule } from 'ng-zorro-antd/message';
import { NzTableModule } from 'ng-zorro-antd/table';

registerLocaleData(en);

@NgModule({
  declarations: [
    AppComponent,
    LoginComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
    ReactiveFormsModule,
    // NgZorroModule,
    LoginRoutingModule,
    HttpClientModule,
    BrowserAnimationsModule,
    NzButtonModule,
    NzDividerModule,
    NzFormModule,
    NzInputModule,
    NzMenuModule,
    NzMessageModule,
    NzTableModule,
  ],
  exports: [
    NzButtonModule,
    NzDividerModule,
    NzFormModule,
    NzInputModule,
    NzMenuModule,
    NzMessageModule,
    NzTableModule,
  ],
  providers: [{ provide: NZ_I18N, useValue: en_US }],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
2. 修改app.component.html文件，将组件添加到首页方便我们进行验证

```
<h1>this is ng-zorro demo</h1>
<app-login></app-login>
```
重新运行即可。

## Use Angular CLI

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 12.2.18.


## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

