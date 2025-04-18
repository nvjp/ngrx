 NgRx Angular App
This project is an Angular application using NgRx for state management, effects, and reactive data flow.

🧱 Tech Stack
Angular v19.2.0

NgRx v19.1.0

@ngrx/store

@ngrx/effects

@ngrx/entity

@ngrx/store-devtools

@ngrx/router-store

RxJS

json-server (for mocking REST APIs during development)

🚀 Getting Started
📦 Install Dependencies
npm install
▶️ Run Application
ng serve
App will be live at http://localhost:4200

🧪 Run Mock API Server
npx json-server --watch db.json --port 3000
📁 Project Structure (NgRx Focused)
pgsql
Copy
Edit
src/
│
├── app/
│   ├── store/
│   │   ├── actions/
│   │   ├── reducers/
│   │   ├── selectors/
│   │   └── effects/
│   ├── features/
│   │   └── user/          # Feature-specific state
│   │       ├── user.actions.ts
│   │       ├── user.reducer.ts
│   │       ├── user.effects.ts
│   │       ├── user.selectors.ts
│   │       └── user.model.ts
│   ├── app.module.ts
│   └── app.component.ts
🧠 NgRx Concepts Used


Actions – Define events that describe state changes.

Reducers – Handle state transitions based on actions.

Selectors – Extract and compute data from state.

Effects – Handle side effects like API calls.

Entity – For structured state management of collections.

Devtools – Time-travel debugging with Redux DevTools.

📚 Example
✅ Action

export const loadUsers = createAction('[User] Load Users');
✅ Reducer
on(loadUsersSuccess, (state, { users }) => ({
  ...state,
  users,
  loaded: true
}))
✅ Selector
ts
Copy
Edit
export const selectAllUsers = createSelector(
  selectUserState,
  (state: UserState) => state.users
);
✅ Effect
ts
Copy
Edit
loadUsers$ = createEffect(() =>
  this.actions$.pipe(
    ofType(loadUsers),
    switchMap(() =>
      this.userService.getUsers().pipe(
        map(users => loadUsersSuccess({ users })),
        catchError(error => of(loadUsersFailure({ error })))
      )
    )
  )
);
🛠 Dev Tools
Use Redux DevTools browser extension for real-time debugging.

Enable with StoreDevtoolsModule.instrument() in AppModule.

📦 Build

ng build
📃 License
MIT

Would you like this tailored to a specific use case, like "Todo App", "User Management", or something you're currently building?







