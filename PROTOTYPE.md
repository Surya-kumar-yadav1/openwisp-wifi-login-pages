# Header Unification Prototype — Issue #314

## Problem

The header component in `client/components/header/header.js` maintained 
two completely separate HTML trees — one for desktop and one for mobile. 
Every element was rendered twice:

- Logo rendered twice
- Second logo rendered twice  
- Language buttons rendered twice
- Navigation links rendered twice
- 
## Solution

Replaced the two parallel HTML trees with a single unified structure.
Responsive behavior is now handled entirely via CSS media queries.

## Files Changed

### `client/components/header/header.js`
- Removed `header-desktop` div tree entirely
- Removed `header-mobile` div tree entirely  
- Replaced with single unified HTML structure

### `client/components/header/index.css`
- Removed `.display-none` and `.display-flex` utility classes
- Removed `.header-desktop { display: none }` mobile rule
- Removed `.header-mobile { display: none }` desktop rule
- Added hamburger hidden by default on desktop:
```css
.header-hamburger {
  display: none;
}

### `client/components/header/header.test.js`
Updated tests that were checking desktop-specific class names:
expect(wrapper.find(".header-link")).toHaveLength(2);
expect(wrapper.find(".header-language-btn")).toHaveLength(2);
expect(wrapper.find(".header-logo-image")).toHaveLength(1);


## Test Results

All 366 tests passing after the changes:
```
Test Suites: 23 passed, 23 total
Tests:       366 passed, 366 total
Snapshots:   63 passed, 63 total
Time:        6.727 s
```
## Screenshots
### Desktop View
<img width="1713" height="962" alt="image" src="https://github.com/user-attachments/assets/98b15bc2-cf5e-4195-8caa-e1b894124088" />

### Mobile View — Menu Closed
<img width="1083" height="970" alt="image" src="https://github.com/user-attachments/assets/afb18535-80f7-4136-bc0e-44023ad6fa42" />

### Mobile View — Menu Open
<img width="1025" height="962" alt="image" src="https://github.com/user-attachments/assets/7ef619a0-0038-4c8a-9f92-18f69c3db219" />


## Branch
- [prototype/unified-header](https://github.com/Surya-kumar-yadav1/openwisp-wifi-login-pages/new/prototype/unified-header)














