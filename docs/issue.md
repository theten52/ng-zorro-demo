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