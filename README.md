# Rust
rustlings exercices


## 00_intro

Code : intro2.rs

Description : the original code had an unknown macro called printline!

```rust
printline!("Hello there!")
```

Fix : To fix the issue, we can change the macro used by :

```rust
println!("Hello !");
```

## 01_variables

Code : variables6.rs

Description : the original code doesn't precise the const type.

```rust
const NUMBER = 3;
```

Fix : To fix the issue, we can add the const type as the following :

```jsx
const NUMBER :i8 = 3;
```

## 02_functions

Code : functions5.rs

Description : the original code had an issue with the return value.

```rust
num * num;
```

Fix : To fix the issue, we should remove the semicolon “;” as the following : 

```rust
return num * num
```

## 03_if

Code : if3.rs

Description : the original code had identifier as random types and Rust doesn't like this

```rust
pub fn animal_habitat(animal: &str) -> &'static str {
    let identifier = if animal == "crab" {
        1
    } else if animal == "gopher" {
        2
    } else if animal == "snake" {
        3
    } else {
        4
    };
```

there are several “if” conditions where we compare “identifier” with integers :

```rust
// DO NOT CHANGE THIS STATEMENT BELOW
    let habitat = if identifier == 1 {
        "Beach"
```

Fix : To fix the issue, all our returns must be integers :

```rust
pub fn animal_habitat(animal: &str) -> &'static str {
    let identifier = if animal == "crab" {
        1
    } else if animal == "gopher" {
        2
    } else if animal == "snake" {
        3
    } else {
        4
    };
```

## 04_primitive_types

Code : primitive_types6.rs

Description : the original code had a missing indexing syntax to access tuple

```rust
// Replace below ??? with the tuple indexing syntax.
    let second = ???;
```

Fix : To fix the issue, we should add the indexing syntax as the following :

```rust
let second = numbers.1;
```

## 05_vecs

Code : vecs2.rs

Description : the original code had two missing part to fill ( 2 loops ):

```rust
fn vec_loop(mut v: Vec<i32>) -> Vec<i32> {
	for element in v.iter_mut() {
        // TODO: Fill this up so that each element in the Vec `v` is
        // multiplied by 2.
        ???
    
	}
```

```rust
fn vec_map(v: &Vec<i32>) -> Vec<i32> {
    v.iter().map(|element| {
        // TODO: Do the same thing as above - but instead of mutating the
        // Vec, you can just return the new number!
        ???
    }).collect()
}
```

Fix : To fix the issue, we should complete those functions :

```rust
fn vec_loop(mut v: Vec<i32>) -> Vec<i32> {
    for element in v.iter_mut() {
        // TODO: Fill this up so that each element in the Vec `v` is
        // multiplied by 2.
        *element = *element * 2;
    }
```

element represents each individual element of the vector ‘v’.

*element derefernces the reference to the current element, giving us access to the value it references.

We do the same with the second function :

```rust
fn vec_map(v: &Vec<i32>) -> Vec<i32> {
    v.iter().map(|element| {
        // TODO: Do the same thing as above - but instead of mutating the
        // Vec, you can just return the new number!
        return *element * 2
    }).collect()
}
```

## 06_move_semantics

Code : move_semantics6.rs

Description : the original code had issues with references, first, get_char function take the ownership of data variable (which cant work here).

```rust
// Should not take ownership
fn get_char(data: String) -> char {
    data.chars().last().unwrap()
}
```

Then the exam tell us that string_uppercase should take ownership of the variable “data”, but it doesnt work because get_char took it.

```rust
fn string_uppercase(mut data: &String) {
    data = &data.to_uppercase();

    println!("{}", data);
}
```

Fix : To fix the issue, we must make get_char function reference to data variable not taking it ownership

```rust
fn get_char(data: &String) -> char {
    data.chars().last().unwrap()
}
```

Then we should update string_uppercase to make it take the ownership 

```rust
// Should take ownership
fn string_uppercase(mut data: String) {
    data = data.to_uppercase();

    println!("{}", data);
}
```

## 07_structs

Code : structs3.rs

Description : the original code had two missing function :

```rust
fn is_international(&self) -> ??? {
        // Something goes here...
    }

    fn get_fees(&self, cents_per_gram: u32) -> ??? {
        // Something goes here...
    }
```

Fix : To fix the issue, we should add some code to resolve the tests :

```rust
fn is_international(&self) -> bool {
	   if self.sender_country != self.recipient_country{
	        return true;
	   } else {
	        return false;
	   }
}

fn get_fees(&self, mut cents_per_gram: u32) -> u32 {
    cents_per_gram = self.weight_in_grams * cents_per_gram;
    cents_per_gram
}
```

those two functions use &self which is a borrowed refernce to  ‘Package’ structure( to access the fields of the struct).

these added code actions passes the tests.

## 08_enums

Code : enums3.rs

Description : the original code had two missing function :

```rust
enum Message {
    // TODO: implement the message variant types based on their usage below
}

fn process(&mut self, message: Message) {
        // TODO: create a match expression to process the different message variants
        // Remember: When passing a tuple as a function argument, you'll need extra parentheses:
        // fn function((t, u, p, l, e))
}
```

Fix : To fix the issue, we should add some code to resolve the tests :

```rust
enum Message {
    // TODO: implement the message variant types based on their usage below
    ChangeColor((u8, u8, u8)),
    Echo(String),
    Move(Point),
    Quit,
}

fn process(&mut self, message: Message) {
        // TODO: create a match expression to process the different message
        // variants
        // Remember: When passing a tuple as a function argument, you'll need
        // extra parentheses: fn function((t, u, p, l, e))
        match message  {
            Message::ChangeColor((x, y, z))=>self.change_color((x, y, z)),
            Message::Echo(String)=>self.echo(String),
            Message::Move(x)=>self.move_position(x),
            Message::Quit=>self.quit(),
        }

}
```

those two functions use &self which is a borrowed refernce to  ‘Package’ structure. 

these added code actions passes the tests.

## 09_strings

Code : strings4.rs

Description : the original code had multiple missings 

```rust
fn main() {
    ???("blue");
    ???("red".to_string());
    ???(String::from("hi"));
    ???("rust is fun!".to_owned());
    ???("nice weather".into());
    ???(format!("Interpolation {}", "Station"));
    ???(&String::from("abc")[0..1]);
    ???("  hello there ".trim());
    ???("Happy Monday!".to_string().replace("Mon", "Tues"));
    ???("mY sHiFt KeY iS sTiCkY".to_lowercase());
}
```

Fix : To fix the issue, we should add some code to resolve the tests :

```rust
fn main() {
    string_slice("blue"); //string litteral -> string slice
    string("red".to_string()); // String
    string(String::from("hi")); // String
    string("rust is fun!".to_owned()); // to_owned -> String
    string("nice weather".into());
    string(format!("Interpolation {}", "Station")); // format -> String
    string_slice(&String::from("abc")[0..1]); // take a slice from 0..1 -> slice
    string_slice("  hello there ".trim()); // .trim -> slice
    string("Happy Monday!".to_string().replace("Mon", "Tues")); // -> String
    string("mY sHiFt KeY iS sTiCkY".to_lowercase()); // .to_lower -> String
}
```

string_slice takes &str as parameter, which is immutable string slice, while string takes a String as a parameter, which is muttable and allocated data.

## 10_modules

Code : modules3.rs

Description : the original code has a missing use statement

```rust
// TODO: Complete this use statement
use ???
```

Fix : To fix the issue, we should add some code to resolve the tests :

```rust
// TODO: Complete this use statement
use std::time::SystemTime;
use std::time::UNIX_EPOCH;
```

we import those 2 standart modules and the issue is fixed.

## 11_hashmaps

Code : hashmaps3.rs

Description : 

```rust
// TODO: Populate the scores table with details extracted from the
        // current line. Keep in mind that goals scored by team_1
        // will be the number of goals conceded by team_2, and similarly
        // goals scored by team_2 will be the number of goals conceded by
        // team_1.
```

Fix : To fix the issue, we should add some code to resolve the tests by using .entry API to find the values in hashmap, .and_modify to modify the value or .or_insert to insert a value when there isnt.

```rust
let t1 = scores.entry(team_1_name.clone()).or_insert(Team {
            goals_scored: 0,
            goals_conceded: 0,
        });
        (*t1).goals_scored += team_1_score;
        (*t1).goals_conceded += team_2_score;

        let t2 = scores.entry(team_2_name.clone()).or_insert(Team {
            goals_scored: 0,
            goals_conceded: 0,
        });
        (*t2).goals_conceded += team_1_score;
        (*t2).goals_scored += team_2_score;
```

## 12_option

Code : options3.rs

Description : the original code has a an issue with “y” value

```rust
y; // Fix without deleting this line.
```

the match takes ownership of “y”

```rust
match y {
        Some(p) => println!("Co-ordinates are {},{} ", p.x, p.y),
        _ => panic!("no match!"),
    }
```

Fix : To fix the issue, we should only make a reference to “y” without taking it ownership

```rust
match &y {
        Some(p) => println!("Co-ordinates are {},{} ", p.x, p.y),
        _ => panic!("no match!"),
    }
```

## 13_error_handling

Code : errors6.rs

Description : the original code has a missing error function

```rust
impl ParsePosNonzeroError {
    fn from_creation(err: CreationError) -> ParsePosNonzeroError {
        ParsePosNonzeroError::Creation(err)
    }
    // TODO: add another error conversion function here.
    // fn from_parseint...
}
```

Fix : To fix the issue, we should add some code to resolve the tests :

```rust
fn parse_pos_nonzero(s: &str) -> Result<PositiveNonzeroInteger, ParsePosNonzeroError> {
    // TODO: change this to return an appropriate error instead of panicking
    // when `parse()` returns an error.
 
    let x: i64 = s.parse().map_err(ParsePosNonzeroError::from_parse)?;

    PositiveNonzeroInteger::new(x).map_err(ParsePosNonzeroError::from_creation)
}
```

we parse the string `s` into an i64 and handle parsing errors by mapping them to a ParsePosNonzeroError.

If the creation fails, map the error to a ParsePosNonzeroError.

## 14_generics

Code : generics2.rs

Description : the original code support wrapping integer value

```rust
struct Wrapper {
    value: u32,
}

impl Wrapper {
    pub fn new(value: u32) -> Self {
        Wrapper { value }
    }
}
```

Fix : To fix the issue, we will change the type of the Wrapper to “T” which takes any type.

```rust
struct Wrapper<T> {
    value: T,
}

impl<T> Wrapper<T> {
    pub fn new(value: T) -> Self {
        Wrapper { value }
    }
}
```

<T> → Any Type

## 15_traits

Code : traits5.rs

Description : the original code doesnt compile

```rust
Your task is to replace the '??'
```

Fix : To fix the issue, we should add some code  :

```rust

fn some_func(item: impl SomeTrait + OtherTrait) -> bool {
    item.some_function() && item.other_function()
}
```

The parameter implement both SomeTrait and OtherTrait, then we can use functions.
