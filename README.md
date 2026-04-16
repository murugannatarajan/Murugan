Hi there, I'm Murugan Natarajan 👋
Senior Frontend Engineer | 12+ Years of Experience | Angular · Ionic · JavaScript
I'm a results-driven frontend engineer based in India, with a passion for building responsive, high-performance web and mobile applications. I've worked with global clients across 🇮🇳 India, 🇸🇬 Singapore, and 🇲🇾 Malaysia.
---
🚀 About Me
🔭 Currently working as a Senior Product Engineer at Nallas Corp (Client: NBME)
📱 Building cross-platform mobile apps with Ionic and scalable web apps with Angular
🧑‍💼 Experienced in Technical Leadership, Agile/Scrum, and end-to-end SDLC ownership
🌏 Worked with clients like Huawei Technologies, Celcom Malaysia, Citibank Singapore, and Asian Food Channel
🏆 RAMP Award for Work Excellence @ Infosys (2014 & 2015)
---
🛠️ Tech Stack
Frontend
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![jQuery](https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)
Frameworks
![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![Ionic](https://img.shields.io/badge/Ionic-3880FF?style=for-the-badge&logo=ionic&logoColor=white)
![AngularJS](https://img.shields.io/badge/AngularJS-E23237?style=for-the-badge&logo=angularjs&logoColor=white)
Tools & Others
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![JIRA](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white)
![Drupal](https://img.shields.io/badge/Drupal-0678BE?style=for-the-badge&logo=drupal&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Photoshop](https://img.shields.io/badge/Photoshop-31A8FF?style=for-the-badge&logo=adobephotoshop&logoColor=white)
---
💼 Professional Journey
Period	Role	Company / Client
Apr 2023 – Mar 2026	Senior Engineer – Product Engineer	Nallas Corp · NBME
Apr 2021 – Feb 2023	Senior Engineer – Technical Lead	Avacent Solutions · Huawei Technologies
Mar 2020 – Feb 2021	Frontend Developer	ClusterCode Technology · Celcom Malaysia
Nov 2013 – Dec 2017	UI Developer	Infosys · Chennai
Apr 2012 – Sep 2013	Head – Design & Development	Inforich Property
Jul 2011 – Jan 2012	Web Developer	Verinon Technology · Asian Food Channel
Feb 2011 – Jun 2011	Web Developer	Xerago e-biz · Citibank Singapore
---
🎓 Education
🎓 MCA – VEL's College of Science, Madras University (2007–2010) — 77%
🎓 B.Sc. Biochemistry – S.R.M Arts & Science College, Madras University (2004–2007) — 64%
---
⚡ Angular Code Examples
1. Standalone Component (Angular 16+)
A self-contained user card component — no NgModule needed. Uses `CommonModule` and `Input` signal for clean, modern Angular architecture.
```typescript
// user-card.component.ts
import { Component, Input } from '@angular/core';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-user-card',
  standalone: true,
  imports: [CommonModule],
  template: `
    <div class="user-card">
      <img [src]="avatarUrl" [alt]="name" class="avatar" />
      <h3>{{ name }}</h3>
      <p>{{ role }}</p>
      <span class="badge" [ngClass]="isActive ? 'active' : 'inactive'">
        {{ isActive ? 'Active' : 'Inactive' }}
      </span>
    </div>
  `,
  styles: [`
    .user-card { padding: 1rem; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); text-align: center; }
    .avatar    { width: 80px; height: 80px; border-radius: 50%; object-fit: cover; }
    .badge     { padding: 4px 12px; border-radius: 12px; font-size: 0.8rem; font-weight: 600; }
    .active    { background: #d4edda; color: #155724; }
    .inactive  { background: #f8d7da; color: #721c24; }
  `]
})
export class UserCardComponent {
  @Input() name!: string;
  @Input() role!: string;
  @Input() avatarUrl!: string;
  @Input() isActive = true;
}
```
```typescript
// app.component.ts — using the standalone component directly
import { Component } from '@angular/core';
import { UserCardComponent } from './user-card.component';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [UserCardComponent],
  template: `
    <app-user-card
      name="Murugan Natarajan"
      role="Senior Frontend Engineer"
      avatarUrl="https://avatars.githubusercontent.com/u/yourId"
      [isActive]="true"
    />
  `
})
export class AppComponent {}
```
---
2. Reactive Forms — User Registration
A fully validated registration form using `ReactiveFormsModule` with custom password-match validation and real-time error feedback.
```typescript
// register.component.ts
import { Component, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ReactiveFormsModule, FormBuilder, FormGroup, Validators, AbstractControl } from '@angular/forms';

// Custom validator: ensures password and confirmPassword match
function passwordMatchValidator(control: AbstractControl) {
  const password    = control.get('password')?.value;
  const confirm     = control.get('confirmPassword')?.value;
  return password === confirm ? null : { passwordMismatch: true };
}

@Component({
  selector: 'app-register',
  standalone: true,
  imports: [CommonModule, ReactiveFormsModule],
  template: `
    <form [formGroup]="registerForm" (ngSubmit)="onSubmit()" class="form-container">
      <h2>Create Account</h2>

      <!-- Full Name -->
      <div class="field">
        <label>Full Name</label>
        <input formControlName="fullName" placeholder="Murugan Natarajan" />
        <span class="error" *ngIf="f['fullName'].touched && f['fullName'].errors?.['required']">
          Name is required.
        </span>
      </div>

      <!-- Email -->
      <div class="field">
        <label>Email</label>
        <input formControlName="email" type="email" placeholder="you@example.com" />
        <span class="error" *ngIf="f['email'].touched && f['email'].errors?.['email']">
          Enter a valid email address.
        </span>
      </div>

      <!-- Password -->
      <div formGroupName="passwords">
        <div class="field">
          <label>Password</label>
          <input formControlName="password" type="password" placeholder="Min. 8 characters" />
          <span class="error" *ngIf="pw['password'].touched && pw['password'].errors?.['minlength']">
            Password must be at least 8 characters.
          </span>
        </div>

        <div class="field">
          <label>Confirm Password</label>
          <input formControlName="confirmPassword" type="password" placeholder="Re-enter password" />
          <span class="error" *ngIf="registerForm.get('passwords')?.errors?.['passwordMismatch']">
            Passwords do not match.
          </span>
        </div>
      </div>

      <button type="submit" [disabled]="registerForm.invalid">Register</button>

      <div class="success" *ngIf="submitted">
        ✅ Registration successful! Welcome, {{ registerForm.value.fullName }}.
      </div>
    </form>
  `,
  styles: [`
    .form-container { max-width: 420px; margin: 2rem auto; padding: 2rem; border-radius: 10px; box-shadow: 0 4px 16px rgba(0,0,0,0.1); font-family: sans-serif; }
    .field          { margin-bottom: 1rem; display: flex; flex-direction: column; gap: 4px; }
    input           { padding: 10px; border: 1px solid #ccc; border-radius: 6px; font-size: 1rem; }
    .error          { color: #e53935; font-size: 0.8rem; }
    button          { width: 100%; padding: 12px; background: #dd0031; color: white; border: none; border-radius: 6px; font-size: 1rem; cursor: pointer; }
    button:disabled { background: #ccc; cursor: not-allowed; }
    .success        { margin-top: 1rem; color: #2e7d32; font-weight: 600; text-align: center; }
  `]
})
export class RegisterComponent implements OnInit {
  registerForm!: FormGroup;
  submitted = false;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    this.registerForm = this.fb.group({
      fullName: ['', [Validators.required, Validators.minLength(3)]],
      email:    ['', [Validators.required, Validators.email]],
      passwords: this.fb.group({
        password:        ['', [Validators.required, Validators.minLength(8)]],
        confirmPassword: ['', Validators.required]
      }, { validators: passwordMatchValidator })
    });
  }

  // Shortcut getters for cleaner template access
  get f() { return this.registerForm.controls; }
  get pw() { return (this.registerForm.get('passwords') as FormGroup).controls; }

  onSubmit() {
    if (this.registerForm.valid) {
      this.submitted = true;
      console.log('Form Data:', this.registerForm.value);
    }
  }
}
```
---
📫 Get in Touch
![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)
![Phone](https://img.shields.io/badge/Call-+91%206374464686-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)
---
"Building pixel-perfect experiences, one component at a time." ✨
