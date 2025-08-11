```markdown
# Detailed Implementation Plan for Alba Women's Health App

This plan outlines the creation and integration of 10 screens into the Next.js (app router) codebase using TypeScript, Tailwind CSS, and shadcn/ui components. The design uses soft pastel colors, gentle gradients, ample white space, and rounded elements to create a calming, supportive experience with proper error handling and best practices.

---

## 1. New Pages Creation in `/src/app`

### A. Welcome / Landing Screen (`src/app/welcome/page.tsx`)
- **Functionality:**  
  - Render a full-screen container with a gentle sunrise gradient (blush pink → lavender → cream).  
  - Center the app name "Alba" using an elegant serif or script font (e.g. Tailwind’s `font-serif` or custom class).  
  - Display the tagline “Support through every reproductive journey” below the title.  
  - Place a rounded button labeled “Get Started” at the bottom, optionally including a small textual sunrise emoji (🌅) adjacent to the title.
- **Best Practices & Error Handling:**  
  - Ensure responsive design via Tailwind’s responsive classes.  
  - Use semantic HTML tags, and add hover/focus states for the button.
- **Dependencies:**  
  - Use Next.js routing with `<Link>` for navigation to the next screen.

---

### B. Journey Selection Screen (`src/app/journey/page.tsx`)
- **Functionality:**  
  - Display the question “Where are you in your journey?” at the top.  
  - Render five rounded cards (as clickable buttons) with soft pastel backgrounds, each featuring an emoji and label:  
    - 🌱 Trying to Conceive  
    - 🤰 Pregnant  
    - 🕊 Experienced a Miscarriage  
    - 🕯 Experienced a Stillbirth  
    - 👶 Postpartum  
- **Best Practices & Error Handling:**  
  - Use a responsive grid layout; ensure fallback UI if a card fails to render.
- **Dependencies:**  
  - Utilize built-in Tailwind classes and Next.js `<Link>` for navigation.

---

### C. Initial Questionnaire Screen (`src/app/questionnaire/page.tsx`)
- **Functionality:**  
  - Title the page “Let’s Personalize Your Experience.”  
  - Present 2–3 multiple-choice questions:
    - What kind of support are you looking for? (Options: Grief, Anxiety, Confidence)  
    - Have you used meditation before? (Yes regularly / Occasionally / Never)  
    - How are you feeling today? (Display mood emojis: 😊, 😐, 😢, 😠, 😴)
  - Use rounded buttons or radio groups for answer selection.
- **Best Practices & Error Handling:**  
  - Implement form validation with controlled components; show a friendly error if no option is selected.
- **Dependencies:**  
  - Leverage existing UI components from `src/components/ui` (e.g., `button.tsx`, `form.tsx`).

---

### D. Personalized Home Screen (`src/app/home/page.tsx`)
- **Functionality:**  
  - Display a soft greeting (e.g., “Good morning, we’re here for you.”) at the top.
  - **Section 1:** “Daily Meditation” featuring a rounded card titled “Healing After Loss” with a play button.
  - **Section 2:** “Today’s Article” preview card (e.g., “What No One Tells You About Early Pregnancy Loss”) with a “Read” button.
  - Optionally include a row of mood check-in emojis.
- **Best Practices & Error Handling:**  
  - Use card components for consistency.  
  - Validate that interactive elements are accessible and handle click events gracefully.
- **Dependencies:**  
  - Import Card and Button components from `src/components/ui` and use Next.js `<Link>` for page transitions.

---

### E. Meditation Screen (`src/app/meditation/page.tsx`)
- **Functionality:**  
  - Title the screen “Grounding After a Miscarriage.”  
  - Center an audio player element with custom play/pause button(s) and a progress bar.
  - Use an `<audio>` element styled with Tailwind; add an `onError` event handler to display an error message if audio fails to load.
  - Show a calming affirmation text below: “It’s okay to grieve. You are not alone.”
  - Set the background with calming abstract design (via CSS gradient or a subtle wave pattern).
- **Best Practices & Error Handling:**  
  - Handle audio load errors with a fallback UI message.
- **Dependencies:**  
  - Use React hooks for controlling audio state and progress updates.

---

### F. Education Article Screen (`src/app/article/page.tsx`)
- **Functionality:**  
  - Display a scrollable view titled “What No One Tells You About Early Pregnancy Loss.”
  - Segment the content with section headers such as “What’s Normal to Feel” and “What to Ask Your Provider.”
  - Incorporate a highlighted quote box styled with a soft border and background.
  - Optionally, include an illustration by adding an `<img>` tag with:  
    `src="https://placehold.co/600x400?text=Soft+illustration+of+gentle+support+health+article+reading"`  
    with descriptive `alt` text and an inline `onerror` fallback to hide the image if it fails.
  - End with a prompt: “Would you like a meditation to accompany this?” and a corresponding button.
- **Best Practices & Error Handling:**  
  - Use semantic tags and ensure graceful image degradation.
- **Dependencies:**  
  - Reuse UI components for buttons and card-style layouts.

---

### G. Therapist Directory Screen (`src/app/therapists/page.tsx`)
- **Functionality:**  
  - Title: “Find a Bereavement-Informed Therapist.”
  - Render a filter button at the top.
  - List therapist cards where each displays: Therapist Name, Location, Specialty tags (e.g., “Loss & Grief”), and an Email or Call button.
- **Best Practices & Error Handling:**  
  - Implement a fallback state for an empty therapist list.  
  - Ensure accessibility and click feedback.
- **Dependencies:**  
  - Use card and button UI components from the existing library.

---

### H. Mood Check-In Screen (`src/app/mood/page.tsx`)
- **Functionality:**  
  - Title the screen “How are you feeling today?”
  - Display 5–6 rounded mood icons using emojis, each with a text label (e.g., Calm, Numb, Sad, Angry, Tired).
  - Provide a “Next” button for proceeding.
- **Best Practices & Error Handling:**  
  - Ensure each mood option is clickable and focusable with proper ARIA labels.
- **Dependencies:**  
  - Style with Tailwind ensuring mobile responsiveness.

---

### I. Community Screen (`src/app/community/page.tsx`)
- **Functionality:**  
  - Title: “Alba Community” with subheading “You’re not alone. Connect with others who’ve walked a similar path.”
  - Render discussion cards for topics such as:
    - Trying to Conceive  
    - Miscarriage Support  
    - Stillbirth Remembrance  
    - Pregnancy Check-Ins  
    - Postpartum Wellness  
  - Each card shows one or two preview messages or prompts.
  - Place a “Start a Conversation” button at the bottom.
- **Best Practices & Error Handling:**  
  - Handle empty discussions gracefully with a friendly notification.
- **Dependencies:**  
  - Use list/card UI components from the design system.

---

### J. Chatbot Screen (`src/app/chat/page.tsx`)
- **Functionality:**  
  - Title the screen “Ask Alba.”
  - Show a sample conversation with:
    - A user bubble reading “I’m feeling really anxious today.”
    - An AI-generated bubble reading “I hear you. Would you like to try a short meditation for anxiety, or read a gentle article?”
  - Include interactive buttons: [Listen to Meditation] and [Read Article].
  - Design the interface like a modern chat app with rounded chat bubbles and a calming background.
- **Best Practices & Error Handling:**  
  - If integrating an LLM API later, add error handling for failed requests and use a loading state.
- **Dependencies:**  
  - Optionally implement a custom hook (e.g., `useChatbot`) in `src/hooks/` for AI interactions.
  - For LLM integration, use OpenRouter’s endpoint (`https://openrouter.ai/api/v1/chat/completions`) with the default model `anthropic/claude-sonnet-4` (subject to user confirmation) and request the API key via environment variables.

---

## 2. Global Styles and Component Reuse

- **Globals.css:**  
  - Optionally add utility classes for the sunrise gradient (e.g., a custom class `.sunrise-gradient`) and soft-rounded buttons if needed.
  - Ensure integration with Tailwind’s responsive design and dark mode variants.

- **Component Consistency:**  
  - Reuse existing UI components from `src/components/ui` (e.g., Button, Card, Dialog) to maintain a consistent modern aesthetic.
  - Create additional small reusable components (e.g., MoodIcon, JourneyCard) if screen-specific elements repeat.

---

## 3. Error Handling and Best Practices

- **Error Handling:**  
  - Use inline event handlers (e.g., `onError` for `<img>` and `<audio>`) to provide graceful degradation.
  - Validate user input on forms and display friendly error messages.
  - Wrap asynchronous operations (e.g., audio loading, chatbot API calls) in try/catch blocks.

- **Navigation & Accessibility:**  
  - Use Next.js `<Link>` for client-side routing between screens.
  - Ensure all interactive elements are accessible (proper ARIA labels, focus states).

- **AI Feature (Chatbot Integration):**  
  - Plan to integrate with an LLM via OpenRouter using the model `anthropic/claude-sonnet-4`.  
  - The API request structure should use an array of message objects with roles and content as per OpenRouter guidelines.  
  - Request and securely store any API keys (e.g., in a `.env.local` file).  
  - Add a sample test using a curl command and verify the response format.

---

## 4. Testing and Quality Assurance

- **Manual Testing:**  
  - Test each screen for responsiveness and layout consistency, especially on mobile.
  - Validate audio playback controls and error events on the Meditation Screen.
  - Navigate through the pages using Next.js routing and verify interactive elements.

- **Automated Testing:**  
  - Use ESLint and TypeScript for static code analysis.
  - Optionally add integration tests to simulate form submissions and API responses.

---

## Summary
- Created 10 new Next.js pages in `/src/app` for each screen (Welcome, Journey, Questionnaire, Home, Meditation, Article, Therapists, Mood, Community, Chat).  
- Incorporated a calming, supportive design with pastel colors, gentle gradients, soft typography, and rounded elements.  
- Integrated error handling for media elements and form validations.  
- Reused UI components from `src/components/ui` and ensured responsive, accessible navigation with Next.js `<Link>`.  
- Planned an optional AI-powered chatbot using OpenRouter with the `anthropic/claude-sonnet-4` model, including a custom hook for API interactions and proper error handling.  
- Updated global styles in `globals.css` as needed for gradients and component styling.  
- Emphasized best practices in state management, error boundaries, and mobile-first responsive design.
