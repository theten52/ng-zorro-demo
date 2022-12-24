1. NG8002: Can't bind to 'formGroup' since it isn't a known property of 'form'.
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
