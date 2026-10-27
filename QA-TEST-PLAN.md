# Scientific Calculator FX-82 — Accuracy and Usability QA

This checklist is included to make the four recommended verification areas concrete. It is a test plan, not a claim that every case has already passed on a physical phone.

## 1. Key and function coverage

- [ ] Digits 0–9, decimal point, sign, DEL, AC, equals
- [ ] Addition, subtraction, multiplication, division, parentheses and operator precedence
- [ ] SHIFT and ALPHA state indicators and shifted functions
- [ ] sin/cos/tan and sin⁻¹/cos⁻¹/tan⁻¹
- [ ] sinh/cosh/tanh and sinh⁻¹/cosh⁻¹/tanh⁻¹
- [ ] log, ln, powers, square, cube, square root, reciprocal and roots
- [ ] Fraction conversion, EXP, Ans, memory store/recall and M+
- [ ] MODE menus, DEG/RAD/GRA, FIX/SCI/NORM, statistics/regression menus
- [ ] Navigation cursor, replay and worked-example recording

## 2. Reference calculation checks

Run each expression and compare against a trusted scientific calculator in the same angle/display mode:

| Input / setup | Expected result |
|---|---:|
| `2 + 3 × 4` | 14 |
| `(2 + 3) × 4` | 20 |
| `√(81)` | 9 |
| `2^3` | 8 |
| `log(100)` in DEG or RAD mode | 2 |
| `ln(e)` if the interface supports the constant `e` | 1 |
| `sin(30)` in DEG mode | 0.5 |
| `sin⁻¹(0.5)` in DEG mode | 30 |
| `1 ÷ 0` | Error/invalid result, not Infinity presented as a normal answer |

Also check very large/small values, negative values, missing parentheses and invalid domains.

## 3. Modes and expression handling

- [ ] Switch DEG → RAD → GRA and verify trigonometric results change correctly.
- [ ] Verify SHIFT inverse functions use the active angle mode correctly.
- [ ] Verify parentheses and unary minus precedence, including `-2^2` and `(-2)^2`.
- [ ] Verify repeated equals, Ans continuation, DEL at the cursor, and AC after an error.
- [ ] Verify FIX, SCI and NORM formatting without changing the underlying numeric result.

## 4. Touch, rapid-input and responsive behavior

- [ ] Rapidly tap number and operator keys; verify no missing or duplicated input.
- [ ] Tap SHIFT then a shifted function; verify the modifier is consumed/reset correctly.
- [ ] Tap buttons near screen edges on narrow phones; verify no horizontal scrolling or clipped keys.
- [ ] Confirm click animation, beep and vibration on supported devices; note that iOS Safari may ignore web vibration.
- [ ] Check keyboard input on desktop and browser refresh after a calculation.

## Current automated checks

- JavaScript syntax: checked with `node --check` for `calculator.js`, `lcd-display.js`, and `recorder.js`.
- Full interactive regression suite: not run automatically in this package; use the cases above for browser/device verification before claiming physical-calculator parity.
