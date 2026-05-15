# API Contracts

Web routes (Blade views). No REST API routes configured.

## Conventions
- Base URL: `http://localhost:8000`
- Auth: Laravel Breeze (session-based, Blade)
- Error format: HTTP status + Blade error page
- Pagination: not configured
- Versioning/compatibility: not applicable

## Routes

### Web (public)
| Method | Path | Controller/Action | Middleware | Notes |
|---|---|---|---|---|
| GET | `/` | `view:welcome` | web | Landing page |
| GET | `/dashboard` | `view:dashboard` | web, auth, verified | User dashboard |

### Profile (authenticated)
| Method | Path | Controller/Action | Middleware | Notes |
|---|---|---|---|---|
| GET | `/profile` | `ProfileController@edit` | web, auth | Edit profile form |
| PATCH | `/profile` | `ProfileController@update` | web, auth | Update profile |
| DELETE | `/profile` | `ProfileController@destroy` | web, auth | Delete account |

### Auth (guest)
| Method | Path | Controller/Action | Middleware | Notes |
|---|---|---|---|---|
| GET | `/register` | `RegisteredUserController@create` | web, guest | Registration form |
| POST | `/register` | `RegisteredUserController@store` | web, guest | Create account |
| GET | `/login` | `AuthenticatedSessionController@create` | web, guest | Login form |
| POST | `/login` | `AuthenticatedSessionController@store` | web, guest | Authenticate |
| GET | `/forgot-password` | `PasswordResetLinkController@create` | web, guest | Password reset request |
| POST | `/forgot-password` | `PasswordResetLinkController@store` | web, guest | Send reset email |
| GET | `/reset-password/{token}` | `NewPasswordController@create` | web, guest | Reset password form |
| POST | `/reset-password` | `NewPasswordController@store` | web, guest | Execute password reset |

### Auth (authenticated)
| Method | Path | Controller/Action | Middleware | Notes |
|---|---|---|---|---|
| GET | `/verify-email` | `EmailVerificationPromptController` | web, auth | Verify notice |
| GET | `/verify-email/{id}/{hash}` | `VerifyEmailController` | web, auth, signed, throttle:6,1 | Verify email |
| POST | `/email/verification-notification` | `EmailVerificationNotificationController@store` | web, auth, throttle:6,1 | Resend verification |
| GET | `/confirm-password` | `ConfirmablePasswordController@show` | web, auth | Confirm password form |
| POST | `/confirm-password` | `ConfirmablePasswordController@store` | web, auth | Confirm password |
| PUT | `/password` | `PasswordController@update` | web, auth | Update password |
| POST | `/logout` | `AuthenticatedSessionController@destroy` | web, auth | Logout |

## Compatibility Notes
- No versioned API endpoints. All routes are Blade-rendered HTML.
