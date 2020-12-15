# JSON Web Tokens (JWT)

```bash
ng g c login
```

=== "src/app/login/login.component.ts"
	```javascript linenums="1"
	import { Component, OnInit } from '@angular/core';
	import {FormBuilder, FormGroup, Validators} from '@angular/forms';
	import {Router} from '@angular/router';

	@Component({
	  selector: 'app-login',
	  templateUrl: './login.component.html',
	  styleUrls: ['./login.component.css']
	})
	export class LoginComponent implements OnInit {
	  form: FormGroup;

	  constructor(private fb: FormBuilder,
	              private authService: AuthService,
	              private router: Router) {
	    this.form = this.fb.group(
	      {
	        email: ['', Validators.required],
	        password: ['', Validators.required],
	      }
	    );
	  }

	  ngOnInit(): void {
	  }

	  login(): void {
	    const val = this.form.value;

	    if (val.email && val.password) {
	      this.authService.login(val.email, val.password)
	        .subscribe(
	          () => {
	            console.log('User is logged in');
	            this.router.navigateByUrl('/');
	          }
	        );
	    }
	  }

	}
	```

=== "src/app/login/login.component.html"
	```html linenums="1"
	<form [formGroup]="form">
	  <fieldset>
	    <legend>Login</legend>
	    <div class="form-group row">
	      <label for="inpEmail" class="col-sm-2 col-form-label">Email: </label>
	      <div class="col-sm-10">
	        <input type="email" class="form-control" formControlName="email" id="inpEmail" readonly>
	      </div>
	    </div>

	    <div class="form-group row">
	      <label for="inpPwd" class="col-sm-2 col-form-label">Password: </label>
	      <div class="col-sm-10">
	        <input type="password" class="form-control" formControlName="password" id="inpPwd" readonly>
	      </div>
	    </div>

	  </fieldset>
	  <div class="form-buttons">
	    <button class="button button-primary"
	            (click)="login()">Login</button>
	  </div>
	</form>
	```

`AuthService` noch nicht existent.

```bash
ng g s shared/auth
```

=== "src/app/shared/auth.service.ts"
	```javascript linenums="1"
	import { Injectable } from '@angular/core';
	import {HttpClient} from '@angular/common/http';

	@Injectable({
	  providedIn: 'root'
	})
	export class AuthService {

	  constructor(private http: HttpClient) {
	  }

	  login(email:string, password:string ): void {
	    return this.http.post<User>('/api/login', {email, password})
	      // this is just the HTTP call,
	      // we still need to handle the reception of the token
	      .shareReplay();
	  }
	}
	```
	