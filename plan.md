Below is a detailed implementation plan for the “Carmovil” contact app. This plan covers all dependent files and outlines changes step by step while ensuring modern UI design, proper error handling, and best practices.

---

**1. Create the Homepage (src/app/page.tsx)**

- **Purpose:**  
  – Acts as the landing page displaying the app header, logo, contact details, and available vehicle list.

- **Changes Required:**  
  – Create a new file if it doesn’t exist.  
  – Import the new components (ContactInfo and VehicleList).  
  – Add a header section that shows the app name “Carmovil” and a logo image with a placeholder URL in the `<img>` tag.  
  – Use an `onError` handler on the image for graceful fallback.  
  – Divide the content into semantic sections (header, main) with modern typography and spacing.

- **Code Outline:**

```typescript
// src/app/page.tsx
import React from "react";
import ContactInfo from "@/components/ContactInfo";
import VehicleList from "@/components/VehicleList";

const HomePage = () => {
  return (
    <div className="min-h-screen bg-gray-50 text-gray-800 font-sans">
      <header className="flex flex-col items-center py-8 bg-white shadow">
        <img
          src="https://placehold.co/150x150?text=Modern+minimalist+Alfa+Romeo+98+car+logo+design+with+sleek+lines+and+bold+colors"
          alt="Modern minimalist Alfa Romeo 98 car logo design featuring sleek lines and bold colors"
          onError={(e) => {
            e.currentTarget.onerror = null;
            e.currentTarget.src = "https://placehold.co/150x150?text=Logo+Not+Found";
          }}
          className="w-36 h-36 object-cover"
        />
        <h1 className="mt-4 text-3xl font-bold">Carmovil</h1>
      </header>
      <main className="p-6 space-y-8">
        <section aria-label="Contacto">
          <ContactInfo />
        </section>
        <section aria-label="Autos Disponibles">
          <VehicleList />
        </section>
      </main>
    </div>
  );
};

export default HomePage;
```

---

**2. Create the Contact Information Component (src/components/ContactInfo.tsx)**

- **Purpose:**  
  – Displays the contact details for the remis service.

- **Changes Required:**  
  – Create a functional component that renders a styled card with the phone number and email.  
  – Use semantic HTML (heading and paragraphs) and add responsive spacing and modern styling.  
  – Handle potential missing data by using defaults (hard-coded values in this case).

- **Code Outline:**

```typescript
// src/components/ContactInfo.tsx
import React from "react";

const ContactInfo = () => {
  const phone = "1126178803";
  const email = "valenjoel080@gmail.com";

  return (
    <div className="max-w-md mx-auto p-6 bg-white rounded-lg shadow border">
      <h2 className="text-2xl font-semibold mb-4">Contacto</h2>
      <p className="text-lg">
        <strong>Teléfono:</strong> {phone}
      </p>
      <p className="text-lg mt-2">
        <strong>Email:</strong> {email}
      </p>
    </div>
  );
};

export default ContactInfo;
```

---

**3. Create the Vehicle List Component (src/components/VehicleList.tsx)**

- **Purpose:**  
  – Show a list of the available vehicles in a modern card design.

- **Changes Required:**  
  – Create a functional component that maps over an array of vehicle names (i.e. "Orion 98", "Alfa Romeo 98", "Siena Fire 2007").  
  – Use a list or grid layout with each item styled as a responsive card.  
  – Ensure proper use of keys when rendering lists and add modern spacing and color contrast.

- **Code Outline:**

```typescript
// src/components/VehicleList.tsx
import React from "react";

const vehicles = ["Orion 98", "Alfa Romeo 98", "Siena Fire 2007"];

const VehicleList = () => {
  return (
    <div className="max-w-2xl mx-auto">
      <h2 className="text-2xl font-semibold mb-4">Autos Disponibles</h2>
      <ul className="grid grid-cols-1 gap-4">
        {vehicles.map((vehicle, index) => (
          <li
            key={index}
            className="p-4 bg-white rounded-lg shadow border hover:shadow-md transition duration-200"
          >
            {vehicle}
          </li>
        ))}
      </ul>
    </div>
  );
};

export default VehicleList;
```

---

**4. Update Global Styles (src/app/globals.css)**

- **Purpose:**  
  – Ensure the entire app follows a modern, clean, and responsive design.

- **Changes Required:**  
  – If not already present, add global styles for background color, font-family, and spacing.  
  – Use CSS classes (or Tailwind if available) to set a consistent visual hierarchy and responsiveness across the app.

- **Example:**

```css
/* src/app/globals.css */
body {
  margin: 0;
  padding: 0;
  background-color: #f9fafb;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
}
```

---

**5. Testing and Error Handling**

- **Action Items:**  
  – Test the homepage to ensure the logo image loads and falls back gracefully with the onError handler.  
  – Validate that the ContactInfo and VehicleList components render properly with the correct styling and spacing.  
  – Ensure the layout remains robust on various screen sizes.

---

**Summary:**  
- Created a homepage (src/app/page.tsx) with a header featuring the “Carmovil” name and a modern Alfa Romeo 98 logo.  
- Developed ContactInfo (src/components/ContactInfo.tsx) to display the phone and email details.  
- Built VehicleList (src/components/VehicleList.tsx) to list the available vehicles (Orion 98, Alfa Romeo 98, Siena Fire 2007).  
- Updated globals.css for clean, modern UI styling with responsive design.  
- Incorporated error handling for the logo image with an onError fallback.  
- The UI uses modern typography, spacing, and semantic sections for intuitive user experience.
