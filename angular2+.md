Style Guides and Coding Standard for Angular 2+
===============================================


Referenced Style Guides
-----------------------

* John Papa Angular 2+ Style Guide:  
    https://angular.io/docs/ts/latest/guide/style-guide.html


Custom extensions
-----------------

### Service CRUD member function names

* Do use `create` for creating function names
* Do use `read` for reading function names.
* Do use `update` for updating function names.
* Do use `delete` for deleting function names.

Example of a user service:
```javascript
@Injectable()
export class UserService {
    createUser(user)     : void { /* ... */  }
    createUsers(users)   : void { /* ... */  } // rather unlikely, for population
    readUser(userId)     : void { /* ... */  }
    readUsers(userIds)   : void { /* ... */  }
    updateUser(user)     : void { /* ... */  }
    updateUsers(users)   : void { /* ... */  }
    deleteUser(userId)   : void { /* ... */  }
    deleteUsers(userIds) : void { /* ... */  }
}
```


### Component CRUD member function names

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
    doCreateUser(user)     : void { /* ... */  }
    doCreateUsers(users)   : void { /* ... */  } // rather unlikely, for population
    doReadUser(userId)     : void { /* ... */  }
    doReadUsers(userIds)   : void { /* ... */  }
    doUpdateUser(user)     : void { /* ... */  }
    doUpdateUsers(users)   : void { /* ... */  }
    doDeleteUser(userId)   : void { /* ... */  }
    doDeleteUsers(userIds) : void { /* ... */  }
}
```
