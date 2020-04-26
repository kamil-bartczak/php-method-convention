# Konwencja nazw metod w PHP
## Wymagania
* PHP > 7.3 

## 1.Metody należy zaczynać od czasownika
```php
//bad
public function firstName()
{

}


//good
public function getFirstName()
{

}

```
### 1.2 Podstawowe czasowniki
|Czasownik  |Opis  |Przykład  | Zwraca
|--|---|---|---|
|get   | Pobierz dane  | getUserPosts()  | string/int/float/array/object/null
|set   | Ustaw dane  | setFirstName()  | self/null
|is   | Zwraca stan  | isUserAuthenticated()  | boolean
|count   | Przelicza dane  | countUsersPosts()  | int/float



## 2 Zwracaj typ

```php
//bad
public function getFirstName()
{
    return 'foo bar';
}

//better

/*
* @return string Get user name.
*/
public function getFirstName()
{

    return 'foo bar';
}


//the best
public function getFirstName(): string
{

    return 'foo bar';
}

```

## 3 Typuj argumenty

```php
//bad

public function getUserById($id)
{

}

//better

/*
* @param int $id User id.
*/
public function getFirstName($id)
{

}

//the best
public function getFirstName(int $id)
{

}

```

## 4 Nie używaj flag w metodach, twórz nowe metody

```php
//bad
public function getCarsName($used = true)
{

}

//good
public function getUsedCarsName()
{

}

public function getNewCarsName()
{

}

```
## 5 Nie używaj skrótów
```php
//bad
public function calcAbsNum()
{

}

//good

public function calculateAbsoluteNumber()
{

}
```

## 6 Rozbijaj dużą funkcjonalność na wiele małych
```php
//bad
public function calculateValueByAddingAndMultiplying($ourNumber, $a, $b)
{

}


//good
public function add(int $baseNumber, int $number)
{

} 

public function multiply(int $baseNumber, int $number)
{

}

```

## 7 Przekazuj jako argument zmienne proste zapisane jako stałe, nie przekazuj ich w prost
```php
//bad
myFunnyFunction(4, [], true, 'qwerty');

//good
myFunnyFunction(User::ADMIN_USER_ID, Response::EMPTY_HEADER,Response::JSON, Keyboard::QWERTY_KEYBOARD);
```

## 8 Nie twórz zbyt ogólnych nazw
```php
//bad
public function getData()
{

}

//better
public function getUserData()
{

}

//the best
public function getUserProfileDetails()
{

}
```


## 9 Nie twórz zbyt dokładnych nazw (zmniejsza re-używalność metod)
```php
//bad
public function getUserProfileDetailsSortedByUserNameAndUserEmail()
{

}

//better
public function getSortedUserProfileDetails()
{

}

//the best
public function getUserProfileDetails(string $sortedBy)
{

}
```

## 10 Jeżeli tylko możesz skracaj nazwy metod
```php
//bad
public function getUserFriendsFromDatabase()
{

}

//good
public function getUserFriends()
{

}