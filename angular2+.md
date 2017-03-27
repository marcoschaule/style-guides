Style Guides and Coding Standard for Angular 2+
===============================================


Referenced Style Guides
-----------------------

* John Papa Angular 2+ Style Guide:  
    https://angular.io/docs/ts/latest/guide/style-guide.html


Custom extensions and overrides
-------------------------------

### Naming conventions


#### Underscore for private members

* DO use an underscore for private members variables and functions!
  _Why?_ Since there is no way (yet) for the template to differ between
  public and private members and since in development the compiler
  won't complain (yet) about the usage of privates, the underscore
  identifies private members on sight.


#### Service CRUD member function names

* Do use `create` for creating function names
* Do use `read` for reading function names.
* Do use `update` for updating function names.
* Do use `delete` for deleting function names.

Example of a user service and observables:
```javascript
@Injectable()
export class UserService {
    createUser(user: UserNew)      : Observable<User>    { /* ... */ }
    createUsers(users: UserNew[])  : Observable<User[]>  { /* ... */ } // rather unlikely, for population
    readUser(userId: number)       : Observable<User>    { /* ... */ }
    readUsers(userIds?: number[])  : Observable<User[]>  { /* ... */ }
    updateUser(user: User)         : Observable<User>    { /* ... */ }
    updateUsers(users: User[])     : Observable<User[]>  { /* ... */ }
    deleteUser(userId: number)     : Observable<Boolean> { /* ... */ }
    deleteUsers(userIds?: number[]): Observable<Boolean> { /* ... */ }
}
```

Example of a user service and promises:
```javascript
@Injectable()
export class UserService {
    createUser(user: UserNew)      : Promise<User>    { /* ... */ }
    createUsers(users: UserNew[])  : Promise<User[]>  { /* ... */ } // rather unlikely, for population
    readUser(userId: number)       : Promise<User>    { /* ... */ }
    readUsers(userIds?: number[])  : Promise<User[]>  { /* ... */ }
    updateUser(user: User)         : Promise<User>    { /* ... */ }
    updateUsers(users: User[])     : Promise<User[]>  { /* ... */ }
    deleteUser(userId: number)     : Promise<Boolean> { /* ... */ }
    deleteUsers(userIds?: number[]): Promise<Boolean> { /* ... */ }
}
```


#### Component CRUD member function names

* Do use `doCreate` for creating function names
* Do use `doRead` for reading function names.
* Do use `doUpdate` for updating function names.
* Do use `doDelete` for deleting function names.
* Do use the `do` prefix to differ component functions from
  service functions.

Example of a user service:
```javascript
@Component({
    // ...
})
export class UserComponent {
    doCreateUser(user: User)        : void { /* ... */ }
    doCreateUsers(users: User[])    : void { /* ... */ } // rather unlikely, for population
    doReadUser(userId: number)      : void { /* ... */ }
    doReadUsers(userIds: number[])  : void { /* ... */ }
    doUpdateUser(user: User)        : void { /* ... */ }
    doUpdateUsers(users: User[])    : void { /* ... */ }
    doDeleteUser(userId: number)    : void { /* ... */ }
    doDeleteUsers(userIds: number[]): void { /* ... */ }
}
```
