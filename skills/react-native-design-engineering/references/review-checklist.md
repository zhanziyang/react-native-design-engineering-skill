# Review Checklist

Use this checklist for evidence-based audits of Expo or React Native motion and touch interactions. Inspect code, installed versions, and runtime observations before assigning a finding.

## Priorities

| Priority | Meaning |
| --- | --- |
| Blocker | Prevents the interaction from working, creates severe accessibility/data-loss risk, or uses an impossible native implementation. |
| High | Causes frequent failure, broken gesture ownership, inaccessible completion, or materially misleading feedback. |
| Medium | Degrades clarity, interruption, physicality, performance, or platform consistency in a meaningful but recoverable way. |
| Low | Minor polish, consistency, or maintainability issue with limited user impact. |

## Categories

- **Purpose/frequency:** Identify what motion communicates and whether its amplitude, duration, repetition, and haptics fit how often the action occurs.
- **Response/timing:** Confirm immediate press-down response, bounded durations, mounted exits, and state changes that do not wait on decoration.
- **Physicality:** Match timing, spring, or decay to the behavior; reserve bounce for momentum or intentional play.
- **Direct manipulation:** Check continuous 1:1 tracking before deliberate resistance, stable activation, dominant-axis intent, velocity projection, and snap/commit thresholds.
- **Interruption:** Check re-grab from the current presentation value, cancellation/finalization, superseded callbacks, and valid recovery destinations.
- **Gesture conflicts:** Establish ownership with scrolling, nested sheets, navigation gestures, parent recognizers, Safe Area, and keyboard changes.
- **Performance:** Prefer UI-thread shared values and transform/opacity per frame; inspect deliberate layout transitions, list virtualization, low-end device behavior, and dropped frames.
- **Accessibility:** Check Reduce Motion equivalents, non-gesture alternatives, roles/state, focus, announcements, touch targets, and non-motion communication.
- **Haptics:** Require causal, supported, restrained feedback at commit/snap/success/warning/error only; reject per-frame or blanket haptics.
- **Platform consistency:** Check iOS and Android differences explicitly without assuming identical haptics, back behavior, keyboard, scrolling, blur/material, or elevation.
- **Verification:** Record the inspected version, platform, device/simulator, build mode, scenario, and remaining unverified states.

## Failure patterns

Flag these only when the evidence demonstrates them:

- JS-thread per-frame React state updates.
- Web-only APIs such as CSS transitions, DOM events, WAAPI, browser media queries, Framer Motion, or Pointer Events in native code.
- Non-interruptible completion or restart from a stale logical endpoint.
- Ignored velocity in gesture release decisions.
- Excessive bounce, especially for frequent actions.
- Blanket or per-frame haptics.
- Missing reduced-motion behavior or a substitute that removes essential state communication.
- Layout/scroll conflict, including unowned nested gestures, keyboard-obscured snap points, or virtualization churn.
- Unverified platform or device claims presented as observed behavior.

## Findings format

Use exactly:

| Priority | Current behavior | Recommended change | Why | Verification |
| --- | --- | --- | --- | --- |

Keep each row evidence-linked. Put observable behavior or code location in **Current behavior**, a minimal actionable fix in **Recommended change**, user/engineering impact in **Why**, and a reproducible check plus platform state in **Verification**.

## Verdict contract

After the table, give a verdict containing:

1. **Overall quality:** concise assessment grounded in the findings.
2. **Top risk:** the highest-impact validated issue or evidence gap.
3. **Highest-value next action:** the single action that most improves quality or confidence.

## Evidence rule

Do not invent findings, runtime behavior, library support, or platform differences. If code, dependency versions, configuration, a reproduction, or runtime observation is missing, request that evidence and mark the relevant state unverified instead of converting an assumption into a finding.
