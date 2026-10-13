# Valid Parentheses

## Problem Information
- **Platform:** Leetcode
- **Difficulty:** Easy
- **URL:** https://leetcode.com/problems/valid-parentheses/submissions/2171320241/
- **Date:** 2026-10-13

## Solution

```text
package main

import (
	"errors"
	"fmt"
)

// Stack represents a LIFO stack using Go generics
type Stack[T any] struct {
	elements []T
}

// Push adds an element to the top of the stack
func (s *Stack[T]) Push(value T) {
	s.elements = append(s.elements, value) // O(1) amortized
}

// Pop removes and returns the top element of the stack
func (s *Stack[T]) Pop() (T, error) {
	var zero T
	if s.IsEmpty() {
		return zero, errors.New("stack is empty")
	}
	
	// Get the last element
	index := len(s.elements) - 1
	value := s.elements[index]
	
	// Prevent memory leaks: erase the element before slicing
	// (Crucial if T contains pointers or objects)
	s.elements[index] = zero 
	
	s.elements = s.elements[:index]
	return value, nil
}

// Peek returns the top element without removing it
func (s *Stack[T]) Peek() (T, error) {
	var zero T
	if s.IsEmpty() {
		return zero, errors.New("stack is empty")
	}
	return s.elements[len(s.elements)-1], nil
}

// IsEmpty checks if the stack has no elements
func (s *Stack[T]) IsEmpty() bool {
	return len(s.elements) == 0
}

func isOpen(r rune) bool {
    switch (r) {
        case '(', '[', '{':
        return true
    }
    return false;
}

func getMatching(r rune) rune {
    switch (r) {
        case ')':
        return '('
        case ']':
        return '['
        case '}':
        return '{'
    }
    return '!'
}

func isValid(s string) bool {
    stk := Stack[rune]{}

    for _, r := range s {
        if isOpen(r) {
            stk.Push(r)
            continue
        }
        if top, err := stk.Pop(); err != nil || top != getMatching(r) {
            return false
        }
    }
    return stk.IsEmpty()
}
```

---
*Generated automatically by LeetFeedback Extension*
