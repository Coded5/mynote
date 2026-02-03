---
id: AI_Note
aliases: []
tags:
  - University
---

```Prolog
```
## Homework 4A

```Prolog
%Variant
member_of(X, [X|_]).
member_of(X, [_|T]) :- member_of(X, T).

member_of1(X, [H|_]) :- X = H.
member_of2(X, [_|T]) :- member_of(X, T).
```


>The difference lies entirely in when the unification happens during the resolution process. In Prolog, "matching" the arguments of a call to the head of a predicate is, by definition, unification.
> - Gemini


Write a rule that related any two lists such that one is a prefix of the other,
for example, they are equal up to the length of the shortest.

```Prolog
is_prefix([], _).

is_prefix([H|T], [H|T2]) :-
    is_prefix(T, T2).
```


Using not_member_of/2, define all_differents(List) such that all elements in List are different.

```Prolog
all_unique([]).

all_unique([H|T]) :-
    not_member_of(H, T),
    all_unique(T).
```

### Scheduling Exercise

I have to meet 6 project students in pairs and I have 3 slots in which I can do this, but there are some constraints.

Let's call the students student1 etc and the slots slot1 etc. A higher-numbered slot occurs after a lower-numbered slot.

The phrase "a higher-numbered slot occurs after a lower-numbered slot" means that
the slots are ordered in time, with higher-numbered slots scheduled
later than lower-numbered slots.

For example:
 Slot1 occurs first.
 Slot2 occurs after Slot1.
 Slot3 occurs after Slot2.

This ordering ensures that the slots are sequential and that no higher-numbered slot
(e.g., Slot3) happens before a lower-numbered slot (e.g., Slot1 or Slot2).
It helps in organizing the meetings in a logical, chronological sequence.

The constraints are:
 1. student1 must meet in slot1.
 2. student2 and student3 must meet in the same slot.
 3. student1 and student4 cannot meet in the same slot.
 4. student6 cannot meet in slot1 or slot3.

I should meet each student exactly once.

I have written the following program for you to solve the scheduling puzzle.

```Prolog

student(student1).
student(student2).
student(student3).
student(student4).
student(student5).
student(student6).

slot(slot1).
slot(slot2).
slot(slot3).

constraint1(Slot1, _Slot2, _Slot3) :-
    member(student1-_, Slot1).

constraint2(Slot1, Slot2, Slot3) :-
    (   member(student2-_, Slot1), member(student3-_, Slot1) );
    (   member(student2-_, Slot2), member(student3-_, Slot2) );
    (   member(student2-_, Slot3), member(student3-_, Slot3) ).

constraint3(Slot1, Slot2, Slot3) :-
    \+ ( member(student1-_, Slot1), member(student4-_, Slot1) ),
    \+ ( member(student1-_, Slot2), member(student4-_, Slot2) ),
    \+ ( member(student1-_, Slot3), member(student4-_, Slot3) ).

constraint4(Slot1, _, Slot3) :-
    \+ member(student6-_, Slot1),
    \+ member(student6-_, Slot3).


meetings_one_two_three(Slot1, Slot2, Slot3) :-

    % Generate all possible assignments of students to slots.
    findall( (Slot1, Slot2, Slot3), (

        % Slot 1
        select_two_students(S1_1, S1_2, _Remaining1),
        Slot1 = [S1_1-S1_2, S1_2-S1_1], % Assign to slot 1.
	
        % Slot 2
        select_two_students(S2_1, S2_2, _Remaining2),
        Slot2 = [S2_1-S2_2, S2_2-S2_1], % Assign to slot 2.

        % Slot 3
        select_two_students(S3_1, S3_2, _Remaining3),
        Slot3 = [S3_1-S3_2, S3_2-S3_1], % Assign to slot 3.

        all_different([S1_1, S1_2, S2_1, S2_2, S3_1, S3_2]), % All students must be different.

        constraint1(Slot1, Slot2, Slot3),
        constraint2(Slot1, Slot2, Slot3),
        constraint3(Slot1, Slot2, Slot3),
        constraint4(Slot1, Slot2, Slot3)
    ), Solutions),

    member( (Slot1, Slot2, Slot3), Solutions). % Select one solution.


select_two_students(S1, S2, Remaining) :-
    student(S1),
    student(S2),
    S1 @< S2,    % Ensure we do not generate (A, B) and (B, A) which is essential for efficiency. This condition reduces the search space.
    findall(Other, (student(Other), Other \= S1, Other \= S2), Remaining).


all_different([]).
all_different([H|T]) :-
    \+ member(H,T),
    all_different(T).
```



If you consult and query the knowledge base and input the main predicate at the Prolog prompt, you will get the following:

?- consult(scheduling).
true.

?- meetings_one_two_three(Slot1, Slot2, Slot3).
Slot1 = [student1-student5, student5-student1],
Slot2 = [student4-student6, student6-student4],
Slot3 = [student2-student3, student3-student2].

Why do we get such results?

The S1 @< S2 should have prevented the generation of double pair results, such as student1-student5 and student5-student1 together.

This is redundant. All I need is student1-student5 or student5-student1 but not both.

Can you fix it?

### Solution

Create a `is_meeting/3` predicate and remove redunant swapping of Slot in findall

```Prolog

student(student1).
student(student2).
student(student3).
student(student4).
student(student5).
student(student6).

slot(slot1).
slot(slot2).
slot(slot3).

constraint1(Slot1, _Slot2, _Slot3) :-
    member(student1-_, Slot1).

constraint2(Slot1, Slot2, Slot3) :-
    (   member(student2-_, Slot1), member(student3-_, Slot1) );
    (   member(student2-_, Slot2), member(student3-_, Slot2) );
    (   member(student2-_, Slot3), member(student3-_, Slot3) ).

constraint3(Slot1, Slot2, Slot3) :-
    \+ ( member(student1-_, Slot1), member(student4-_, Slot1) ),
    \+ ( member(student1-_, Slot2), member(student4-_, Slot2) ),
    \+ ( member(student1-_, Slot3), member(student4-_, Slot3) ).

constraint4(Slot1, _, Slot3) :-
    \+ member(student6-_, Slot1),
    \+ member(student6-_, Slot3).


meetings_one_two_three(Slot1, Slot2, Slot3) :-

    % Generate all possible assignments of students to slots.
    findall( (Slot1, Slot2, Slot3), (

        % Slot 1
        select_two_students(S1_1, S1_2, _Remaining1),
        Slot1 = [S1_1-S1_2, S1_2-S1_1], % Assign to slot 1.
	
        % Slot 2
        select_two_students(S2_1, S2_2, _Remaining2),
        Slot2 = [S2_1-S2_2, S2_2-S2_1], % Assign to slot 2.

        % Slot 3
        select_two_students(S3_1, S3_2, _Remaining3),
        Slot3 = [S3_1-S3_2, S3_2-S3_1], % Assign to slot 3.

        all_different([S1_1, S1_2, S2_1, S2_2, S3_1, S3_2]), % All students must be different.

        constraint1(Slot1, Slot2, Slot3),
        constraint2(Slot1, Slot2, Slot3),
        constraint3(Slot1, Slot2, Slot3),
        constraint4(Slot1, Slot2, Slot3)
    ), Solutions),

    member( (Slot1, Slot2, Slot3), Solutions). % Select one solution.


select_two_students(S1, S2, Remaining) :-
    student(S1),
    student(S2),
    S1 @< S2,    % Ensure we do not generate (A, B) and (B, A) which is essential for efficiency. This condition reduces the search space.
    findall(Other, (student(Other), Other \= S1, Other \= S2), Remaining).


all_different([]).
all_different([H|T]) :-
    \+ member(H,T),
    all_different(T).
```

# Homework 4B

## Unification

|term A = term B | A matches B | A unifies B | Remarks |
|------|----|-----|------|
|a = b| no | no | |
|1+1 = 2| no | no | |
|X + Y = 2| no | yes | |
|f(a) = f(a,b)| no | no ||
|f(X, Y) = f(Y, a) | no | yes | X = Y = a (unified)|
|f(X, Y, Z) = f(Y, Z, X) | no | yes | X = Y = Z (unified)|
