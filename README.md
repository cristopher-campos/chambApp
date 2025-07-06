<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>ChambAPP</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Montserrat:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
/* Base colors for the futuristic theme */
:root {
    --primary-color: #00e676; /* Neon Green */
    --primary-dark: #00c853;
    --secondary-color: #2979ff; /* Electric Blue */
    --secondary-dark: #2962ff;
    --accent-color: #e040fb; /* Vibrant Purple */
    --background-dark: #1a1a2e; /* Deep Dark Blue/Purple */
    --background-light: #2c2c4a; /* Slightly lighter dark blue */
    --background-gradient-start: #0f0c29; /* Darkest Blue */
    --background-gradient-end: #302b63;    /* Purple-ish Blue */
    --background-gradient-middle: #24243e; /* Midpoint Blue */
    --text-color-light: #e0e0e0; /* Off-white for readability */
    --text-color-dark: #a0a0a0; /* Greyish for subtle text */
    --card-background: rgba(44, 44, 74, 0.7); /* Translucent dark card */
    --border-color: rgba(0, 230, 118, 0.3); /* Semi-transparent neon green border */
    --glow-color-primary: rgba(0, 230, 118, 0.5); /* Neon Green glow */
    --glow-color-secondary: rgba(41, 121, 255, 0.5); /* Electric Blue glow */
    --shadow-strong: rgba(0, 0, 0, 0.4);
    --shadow-light: rgba(0, 0, 0, 0.2);
    --button-hover-scale: 1.03;

    /* Status colors, updated for futuristic look */
    --status-success: #00e676; /* Neon Green */
    --status-danger: #ff1744;  /* Deep Red */
    --status-warning: #ffea00; /* Bright Yellow */
    --status-info: #2979ff;    /* Electric Blue */
    --status-finalized: #82b1ff; /* Lighter Blue */

    /* Rank colors (can be themed further) */
    --rank-new-color: #616161;
    --rank-student-color: #2979ff;
    --rank-donor-color: #e040fb;
    --rank-creator-color: #7c4dff;
    --rank-owner-color: #ff1744;

    /* Badge colors (similar to status but distinct) */
    --badge-bg-success: #00c853;
    --badge-bg-info: #2962ff;
    --badge-bg-warning: #ffea00;
    --badge-bg-danger: #ff1744;
    --badge-bg-purple: #7c4dff;
}

body {
    font-family: 'Montserrat', sans-serif;
    text-align: center;
    margin: 0;
    padding-top: 60px;
    background: linear-gradient(135deg, var(--background-gradient-start) 0%, var(--background-gradient-middle) 50%, var(--background-gradient-end) 100%);
    background-attachment: fixed;
    color: var(--text-color-light);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    line-height: 1.6;
    overflow-x: hidden; /* Prevent horizontal scroll */
}

h1 {
    font-family: 'Orbitron', sans-serif;
    font-size: 3.5em; /* Larger logo */
    color: var(--text-color-light);
    margin-bottom: 50px;
    text-shadow: 0 0 10px var(--glow-color-primary), 0 0 20px var(--glow-color-primary), 0 0 30px var(--glow-color-secondary);
    letter-spacing: 0.1em; /* Wider spacing for futuristic feel */
    animation: pulseGlow 2s infinite alternate;
    user-select: none;
    -webkit-font-smoothing: antialiased;
}

@keyframes pulseGlow {
    from {
        text-shadow: 0 0 8px var(--glow-color-primary), 0 0 16px var(--glow-color-primary), 0 0 24px var(--glow-color-secondary);
    }
    to {
        text-shadow: 0 0 12px var(--glow-color-primary), 0 0 24px var(--glow-color-primary), 0 0 36px var(--glow-color-secondary);
    }
}

h2, h3 {
    font-family: 'Orbitron', sans-serif;
    margin: 0 0 20px;
    font-weight: 700;
    color: var(--primary-color);
    text-shadow: 0 0 5px rgba(0,230,118,0.3);
    letter-spacing: 0.05em;
}
h2 {
    font-size: 2.2em;
}
h3 {
    font-size: 1.7em;
    color: var(--secondary-color);
    text-shadow: 0 0 4px rgba(41,121,255,0.3);
    letter-spacing: 0.05em;
}

.pantalla {
    display: none;
    animation: fadeIn 0.6s ease-out;
    width: 90%;
    max-width: 600px;
    background: var(--card-background); /* Translucent dark background */
    padding: 35px 45px;
    border-radius: 15px; /* Slightly rounded for modern feel */
    box-shadow: 0 0 25px var(--shadow-strong); /* Stronger shadow/glow */
    margin-bottom: 40px;
    border: 1px solid var(--border-color); /* Neon border */
    backdrop-filter: blur(8px); /* Glassmorphism effect */
    -webkit-backdrop-filter: blur(8px);
    transition: all 0.3s ease-in-out;
    position: relative; /* For the grid pattern */
    overflow: hidden; /* Hide overflowing grid */
}
.pantalla.visible {
    display: block;
}
.pantalla:hover {
    box-shadow: 0 0 35px var(--glow-color-primary); /* More intense glow on hover */
    transform: translateY(-3px);
}

/* Background grid pattern */
.pantalla::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: linear-gradient(0deg, rgba(255,255,255,0.05) 1px, transparent 1px),
                      linear-gradient(90deg, rgba(255,255,255,0.05) 1px, transparent 1px);
    background-size: 25px 25px; /* Size of the grid cells */
    opacity: 0.1;
    z-index: -1;
}


/* New styles for button sections */
.button-section {
    display: flex;
    flex-direction: column; /* Stack buttons vertically by default */
    gap: 15px; /* Space between buttons in a section */
    margin-top: 25px; /* Space above each section */
    width: 100%; /* Take full width of parent */
    align-items: center; /* Center buttons horizontally */
}

.button-section.top-section {
    margin-bottom: 20px; /* Add space below top sections */
}

.button-section.bottom-section {
    margin-top: 30px; /* More space above bottom sections (e.g., logout, back buttons) */
    border-top: 1px dashed rgba(255,255,255,0.1); /* Subtle separator */
    padding-top: 20px;
}

/* Adjust general button margin to be handled by parent .button-section */
button {
    margin: 0; /* Reset default margin */
    padding: 14px 30px;
    font-size: 1.0em;
    cursor: pointer;
    background: linear-gradient(45deg, var(--primary-color) 0%, var(--primary-dark) 100%);
    background-size: 200% auto;
    color: var(--background-dark); /* Darker text for contrast on bright buttons */
    border: none;
    border-radius: 10px;
    transition: all 0.4s ease-in-out;
    box-shadow: 0 5px 15px rgba(0,0,0,0.3), 0 0 10px var(--primary-color); /* Stronger button shadow with glow */
    user-select: none;
    font-weight: 600;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    width: 100%; /* Make buttons take full width within their section */
    max-width: 300px; /* Limit max width for aesthetic */
}
button:hover {
    background-position: right center;
    box-shadow: 0 7px 20px rgba(0,0,0,0.4), 0 0 20px var(--glow-color-primary); /* More intense glow on hover */
    transform: translateY(-2px) scale(var(--button-hover-scale));
}
button:active {
    transform: translateY(0) scale(0.98);
    box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--primary-dark);
}

/* Specific Button Styles to override gradient where not desired */
.btn-accept, .btn-reject, .btn-counter, .btn-calificar, .btn-ocultar-pedido, .btn-eliminar-pedido,
.friend-request button, .friend-item button,
#btn-upload-image {
    background: none;
    background-color: var(--primary-color); /* Default solid color for these */
    transition: all 0.2s ease;
    background-position: unset;
    background-size: auto;
    box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--primary-color); /* Subtle glow */
    color: var(--background-dark); /* Ensure text color is dark for contrast */
}

.btn-accept { background-color: var(--status-success); box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--status-success); }
.btn-accept:hover { background-color: var(--primary-dark); box-shadow: 0 4px 12px rgba(0,0,0,0.3), 0 0 15px var(--status-success); transform: translateY(-1px) scale(1.02);}
.btn-reject { background-color: var(--status-danger); box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--status-danger); }
.btn-reject:hover { background-color: #d8143d; box-shadow: 0 4px 12px rgba(0,0,0,0.3), 0 0 15px var(--status-danger); transform: translateY(-1px) scale(1.02);}
.btn-counter { background-color: var(--status-warning); color: var(--background-dark); box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--status-warning); }
.btn-counter:hover { background-color: #f7d900; box-shadow: 0 44px 12px rgba(0,0,0,0.3), 0 0 15px var(--status-warning); transform: translateY(-1px) scale(1.02);}
.btn-calificar { background-color: var(--accent-color); box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--accent-color); }
.btn-calificar:hover { background-color: #c737e0; box-shadow: 0 44px 12px rgba(0,0,0,0.3), 0 0 15px var(--accent-color); transform: translateY(-1px) scale(1.02);}


input, textarea, select {
    padding: 14px 18px;
    width: calc(100% - 36px);
    margin: 10px 0;
    border: 1px solid rgba(41, 121, 255, 0.5); /* Semi-transparent electric blue border */
    border-radius: 8px;
    font-size: 1em;
    box-sizing: border-box;
    transition: border-color 0.3s ease, box-shadow 0.3s ease, background-color 0.3s ease;
    resize: vertical;
    background-color: rgba(44, 44, 74, 0.5); /* Slightly more translucent */
    color: var(--text-color-light);
    font-family: 'Montserrat', sans-serif;
}
input:focus, textarea:focus, select:focus {
    border-color: var(--secondary-color);
    outline: none;
    box-shadow: 0 0 0 3px rgba(41, 121, 255, 0.4), 0 0 15px var(--glow-color-secondary); /* Electric blue glow on focus */
    background-color: rgba(44, 44, 74, 0.8); /* Less translucent on focus */
}
input::placeholder, textarea::placeholder {
    color: #888; /* Slightly darker placeholder */
}


.pedido, .friend-request, .friend-item {
    border: 1px solid rgba(0, 230, 118, 0.3); /* Neon green border */
    padding: 20px 25px;
    margin: 15px auto;
    background: rgba(44, 44, 74, 0.6); /* Translucent background */
    width: 100%;
    text-align: left;
    border-radius: 12px;
    box-shadow: 0 0 15px rgba(0, 230, 118, 0.2); /* Subtle glow */
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    user-select: none;
    position: relative;
}
.pedido:hover, .friend-request:hover, .friend-item:hover {
    transform: translateY(-4px);
    box-shadow: 0 0 25px rgba(0, 230, 118, 0.4); /* More intense glow on hover */
}

/* Grouping buttons within pedido and friend-item for better layout */
.pedido > div, .friend-item > div {
    display: flex;
    flex-wrap: wrap; /* Allow buttons to wrap on smaller screens */
    gap: 10px; /* Space between buttons */
    margin-top: 15px;
    justify-content: center; /* Center buttons within order/friend item */
}

/* Ensure individual buttons within these flex containers don't override width */
.pedido > div button, .friend-item > div button {
    width: auto; /* Let content dictate width */
    max-width: none; /* No max-width constraint here */
    margin: 0; /* Reset individual button margins */
}


.pedido .btn-mapa,
.pedido .btn-chat,
.friend-item .btn-chat {
    background-color: var(--status-info); /* Electric blue */
    padding: 10px 20px;
    font-size: 0.9em;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(41, 121, 255, 0.3), 0 0 8px var(--status-info); /* Blue glow */
    transition: all 0.2s ease;
    display: inline-block;
    min-width: unset;
    color: var(--background-dark); /* Darker text */
    text-transform: uppercase;
    margin: 0; /* Reset margin from general button style */
}

.pedido .btn-mapa:hover,
.pedido .btn-chat:hover,
.friend-item .btn-chat:hover {
    background-color: var(--secondary-dark);
    transform: translateY(-1px) scale(1.01);
    box-shadow: 0 4px 15px rgba(41, 121, 255, 0.4), 0 0 15px var(--status-info);
}

.pedido.negociacion-pendiente {
    border-color: var(--status-warning);
    box-shadow: 0 0 20px rgba(255, 234, 0, 0.3);
    background-color: rgba(60, 60, 90, 0.7); /* Slightly different translucent bg */
}

.pedido.negociacion-aceptada {
    border-color: var(--status-success);
    box-shadow: 0 0 20px rgba(0, 230, 118, 0.3);
    background-color: rgba(50, 80, 50, 0.7); /* Greenish translucent bg */
}

.pedido.negociacion-rechazada {
    border-color: var(--status-danger);
    box-shadow: 0 0 20px rgba(255, 23, 68, 0.3);
    background-color: rgba(90, 40, 40, 0.7); /* Reddish translucent bg */
}

.pedido .status-badge {
    font-size: 0.85em;
    font-weight: 600;
    padding: 6px 10px;
    border-radius: 6px;
    margin-left: 10px;
    vertical-align: middle;
    color: var(--background-dark); /* Text color for badges */
    text-transform: uppercase;
}

.status-badge.info { background-color: var(--status-info); }
.status-badge.warning { background-color: var(--status-warning); }
.status-badge.success { background-color: var(--status-success); }
.status-badge.danger { background-color: var(--status-danger); }
.status-badge.finalizado { background-color: var(--status-finalized); }


#toast {
    visibility: hidden;
    min-width: 300px;
    background: var(--status-success);
    color: var(--background-dark);
    text-align: center;
    border-radius: 10px;
    padding: 16px 30px;
    position: fixed;
    z-index: 1000;
    left: 50%;
    bottom: 40px;
    font-size: 1.1em;
    transform: translateX(-50%);
    box-shadow: 0 0 20px rgba(0,230,118,0.4); /* Glow effect for toast */
    user-select: none;
    opacity: 0;
    transition: opacity 0.5s, bottom 0.5s;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 600;
}
#toast.show {
    visibility: visible;
    opacity: 1;
    bottom: 60px;
    animation: fadein-toast 0.5s, fadeout-toast 0.5s 2.5s;
}
@keyframes fadeIn {
    from {opacity: 0; transform: translateY(20px);}
    to {opacity: 1; transform: translateY(0);}
}
@keyframes fadein-toast {
    from { bottom: 40px; opacity: 0; }
    to { bottom: 60px; opacity: 1; }
}
@keyframes fadeout-toast {
    from { bottom: 60px; opacity: 1; }
    to { bottom: 40px; opacity: 0; }
}

/* Toast colors */
#toast.success { background: var(--status-success); }
#toast.danger { background: var(--status-danger); }
#toast.warning { background: var(--status-warning); color: var(--background-dark);}
#toast.info { background: var(--status-info); }
#toast .icon {
    margin-right: 10px;
    font-size: 1.4em;
}

.saludo {
    margin-bottom: 25px;
    color: var(--primary-color);
    font-weight: 700;
    font-size: 1.8em;
    user-select: none;
    text-shadow: 0 0 8px rgba(0,230,118,0.4);
    font-family: 'Orbitron', sans-serif;
    letter-spacing: 0.03em;
}
.creditos, .version-info {
    position: fixed;
    bottom: 15px;
    font-size: 0.75em;
    color: rgba(255,255,255,0.4); /* Lighter for subtle effect */
    user-select: none;
    font-weight: 400;
    font-family: 'Montserrat', sans-serif;
    letter-spacing: 0.02em;
}
.creditos { right: 20px; }
.version-info { left: 20px; }

/* Modal */
.modal-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.7); /* Darker, more opaque overlay */
    display: none;
    justify-content: center;
    align-items: center;
    z-index: 2000; /* Higher z-index */
    opacity: 0;
    transition: opacity 0.3s ease;
}
.modal-overlay.visible {
    display: flex;
    opacity: 1;
}
.modal {
    background: rgba(44, 44, 74, 0.85); /* Darker translucent for modals */
    border-radius: 15px;
    padding: 30px 40px;
    max-width: 500px;
    width: 90%;
    box-shadow: 0 0 30px rgba(41, 121, 255, 0.4); /* Blue glow for modals */
    text-align: left;
    transform: translateY(20px);
    opacity: 0;
    transition: transform 0.3s ease, opacity 0.3s ease;
    position: relative;
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    display: flex; /* Ensure modal content is a flex column */
    flex-direction: column; /* Ensure modal content is a flex column */
}
.modal-overlay.visible .modal {
    transform: translateY(0);
    opacity: 1;
}
.modal h3 {
    margin-top: 0;
    font-weight: 700;
    margin-bottom: 20px;
    user-select: none;
    color: var(--secondary-color); /* Electric blue title */
    text-shadow: 0 0 5px rgba(41,121,255,0.4);
}
.modal p {
    margin-bottom: 18px;
    user-select: none;
    font-size: 1em;
    color: var(--text-color-light);
}
.modal-buttons {
    display: flex;
    justify-content: flex-end; /* Align buttons to the right */
    gap: 12px;
    margin-top: 25px;
}
.modal-buttons button {
    padding: 12px 25px;
    font-size: 0.9em;
    border-radius: 8px;
    margin: 0;
    color: var(--background-dark); /* Ensure text is dark */
    width: auto; /* Buttons in modals should not take full width */
    max-width: none;
}

/* Close button for modals */
.modal .close-btn {
    position: absolute;
    top: 15px;
    right: 15px;
    background: none;
    border: none;
    font-size: 1.5em;
    cursor: pointer;
    color: rgba(255,255,255,0.6); /* Lighter for subtle effect */
    padding: 5px;
    transition: color 0.2s ease, text-shadow 0.2s ease;
}
.modal .close-btn:hover {
    color: var(--primary-color); /* Neon green on hover */
    text-shadow: 0 0 8px var(--primary-color);
}


.direccion-input-group {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 10px 0;
    flex-wrap: wrap;
}
.direccion-input-group input {
    flex-grow: 1;
    margin: 0;
}
.direccion-input-group button {
    margin: 0;
    padding: 12px 18px;
    font-size: 0.9em;
    white-space: nowrap;
    box-shadow: 0 2px 8px rgba(41, 121, 255, 0.3), 0 0 5px var(--secondary-color);
    background-color: var(--secondary-color);
    color: var(--background-dark);
    width: auto;
    max-width: none;
}
.direccion-input-group button:hover {
    background-color: var(--secondary-dark);
    box-shadow: 0 4px 12px rgba(41, 121, 255, 0.4), 0 0 15px var(--secondary-color);
}

.btn-ocultar-pedido {
    background-color: #555; /* Darker grey */
    box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    color: var(--text-color-light); /* Lighter text */
}
.btn-ocultar-pedido:hover {
    background-color: #444;
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
}

.btn-eliminar-pedido {
    background-color: var(--status-danger);
    box-shadow: 0 2px 8px rgba(255, 23, 68, 0.3), 0 0 5px var(--status-danger);
}
.btn-eliminar-pedido:hover {
    background-color: #d8143d;
    box-shadow: 0 4px 12px rgba(255, 23, 68, 0.4), 0 0 15px var(--status-danger);
}

/* Chat styles */
#modal-chat .modal, #modal-friend-chat .modal {
    max-width: 550px;
    display: flex;
    flex-direction: column;
    max-height: 85vh;
}
#chat-messages, #friend-chat-messages {
    flex-grow: 1;
    border: 1px solid rgba(41, 121, 255, 0.3); /* Blue translucent border */
    padding: 15px;
    min-height: 200px;
    max-height: 400px;
    overflow-y: auto;
    margin-bottom: 15px;
    border-radius: 10px;
    background-color: rgba(26, 26, 46, 0.4); /* Very translucent dark background */
    text-align: left;
    display: flex;
    flex-direction: column;
    gap: 12px;
    box-shadow: inset 0 0 8px rgba(41, 121, 255, 0.1); /* Subtle inner blue glow */
}
.chat-message {
    padding: 10px 15px;
    border-radius: 15px; /* More rounded bubbles */
    max-width: 90%;
    word-wrap: break-word;
    font-size: 0.95em;
    position: relative;
    color: var(--text-color-light);
}
.chat-message.self {
    background-color: rgba(0, 230, 118, 0.2); /* Translucent green for self */
    align-self: flex-end;
    border-bottom-right-radius: 5px;
    border: 1px solid rgba(0, 230, 118, 0.4);
}
.chat-message.other {
    background-color: rgba(41, 121, 255, 0.2); /* Translucent blue for other */
    align-self: flex-start;
    border-bottom-left-radius: 5px;
    border: 1px solid rgba(41, 121, 255, 0.4);
}
.chat-message strong {
    display: block;
    font-size: 0.85em;
    margin-bottom: 3px;
    color: var(--primary-color);
    font-weight: 700;
}
.chat-message.other strong {
    color: var(--secondary-color);
}
.chat-message small {
    display: block;
    font-size: 0.7em;
    color: #999;
    text-align: right;
    margin-top: 5px;
}
/* Chat Bubble Tail */
.chat-message.self::before {
    content: '';
    position: absolute;
    bottom: 0px;
    right: -8px;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 0 8px 8px;
    border-color: transparent transparent transparent rgba(0, 230, 118, 0.2);
}
.chat-message.other::before {
    content: '';
    position: absolute;
    bottom: 0px;
    left: -8px;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 8px 8px 0;
    border-color: transparent rgba(41, 121, 255, 0.2) transparent transparent;
}


#chat-input-group, #friend-chat-input-group {
    display: flex;
    gap: 10px;
    margin-top: 15px;
}
#chat-input-group input, #friend-chat-input-group input {
    flex-grow: 1;
    margin: 0;
}
#chat-input-group button, #friend-chat-input-group button {
    margin: 0;
    padding: 12px 20px;
    font-size: 0.95em;
    background-color: var(--secondary-color);
    color: var(--background-dark);
    width: auto;
    max-width: none;
}
#chat-input-group button:hover, #friend-chat-input-group button:hover {
    background-color: var(--secondary-dark);
}


/* Friend list and requests */
.friend-request, .friend-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: rgba(44, 44, 74, 0.5); /* Translucent */
    margin-top: 10px;
    margin-bottom: 10px;
    padding: 15px 20px;
    border-radius: 10px;
    border: 1px solid rgba(41, 121, 255, 0.3); /* Blue border */
    box-shadow: 0 0 10px rgba(41, 121, 255, 0.1);
}
.friend-request span, .friend-item span {
    font-weight: 600;
    color: var(--text-color-light);
    flex-grow: 1;
}
.friend-request div, .friend-item div {
    display: flex;
    gap: 8px;
}
.friend-request button, .friend-item button {
    margin: 0;
    padding: 8px 15px;
    font-size: 0.85em;
    border-radius: 8px;
    box-shadow: none;
    transform: none;
    text-transform: uppercase;
    width: auto;
    max-width: none;
}
.friend-request button:hover, .friend-item button:hover {
    transform: none;
    box-shadow: none;
}
.friend-item .btn-mapa {
    background-color: #555;
    color: var(--text-color-light);
    box-shadow: 0 2px 8px rgba(0,0,0,0.2);
}
.friend-item .btn-mapa:hover {
    background-color: #444;
    box-shadow: 0 44px 12px rgba(0,0,0,0.3);
}

/* Add friend button in order list */
.btn-add-friend, .btn-accept-friend-prompt {
    background-color: var(--secondary-color);
    margin-left: 10px;
    padding: 8px 15px;
    font-size: 0.8em;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(41, 121, 255, 0.3);
    color: var(--background-dark);
    width: auto;
    max-width: none;
}
.btn-add-friend:hover, .btn-accept-friend-prompt:hover {
    background-color: var(--secondary-dark);
    box-shadow: 0 44px 12px rgba(41, 121, 255, 0.4);
    transform: translateY(-1px);
}

.perfil-info-item {
    margin-bottom: 15px;
    text-align: left;
}
.perfil-info-item label {
    display: block;
    font-weight: 600;
    margin-bottom: 8px;
    color: var(--text-color-light);
}
.perfil-info-item input[type="checkbox"] {
    width: auto;
    margin-right: 8px;
    transform: scale(1.2);
    vertical-align: middle;
}
.perfil-info-item textarea {
    min-height: 80px;
    max-height: 120px;
    padding: 10px 15px;
    font-size: 0.95em;
}

/* Negotiation History */
.negociacion-historial {
    border-top: 1px dashed rgba(255,255,255,0.2); /* Subtle dashed line */
    margin-top: 15px;
    padding-top: 15px;
    text-align: left;
    font-size: 0.9em;
    color: var(--text-color-dark);
}
.negociacion-historial h4 {
    margin-top: 0;
    margin-bottom: 10px;
    font-size: 1.1em;
    color: var(--text-color-light);
    text-shadow: none;
}
.negociacion-historial div {
    margin-bottom: 6px;
}
.negociacion-historial .oferta-comprador {
    color: var(--secondary-color);
    font-weight: 600;
}
.negociacion-historial .oferta-solicitante {
    color: var(--primary-color);
    font-weight: 600;
}

/* Ranks in Profile */
.perfil-info-item .rank-badge {
    display: inline-block;
    padding: 6px 12px;
    border-radius: 15px;
    font-size: 0.85em;
    font-weight: 600;
    color: var(--background-dark);
    margin-left: 10px;
    vertical-align: middle;
    text-transform: capitalize;
    box-shadow: 0 0 8px rgba(0,0,0,0.2);
}
.rank-badge.new { background-color: var(--rank-new-color); color: var(--text-color-light); }
.rank-badge.student { background-color: var(--rank-student-color); }
.rank-badge.donor { background-color: var(--rank-donor-color); }
.rank-badge.creator { background-color: var(--rank-creator-color); }
.rank-badge.owner { background-color: var(--rank-owner-color); }

/* Profile - Photo and Slogan */
#perfil-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 25px;
}

#perfil-foto-container {
    width: 120px; /* Larger photo */
    height: 120px;
    border-radius: 50%;
    overflow: hidden;
    margin-bottom: 15px;
    border: 3px solid var(--primary-color); /* Thicker neon border */
    box-shadow: 0 0 15px var(--primary-color); /* Neon glow */
    background-color: var(--background-light);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    position: relative;
    transition: all 0.3s ease;
}

#perfil-foto-container:hover {
    box-shadow: 0 0 25px var(--glow-color-primary), 0 0 35px var(--glow-color-secondary); /* Intense glow on hover */
    transform: scale(1.05);
}

#perfil-foto-container:hover::after {
    content: 'Cambiar Foto';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0,0,0,0.6); /* Darker overlay */
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.9em;
    font-weight: 700;
    opacity: 0;
    transition: opacity 0.2s ease;
}

#perfil-foto-container:hover::after {
    opacity: 1;
}

#perfil-foto {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

#perfil-lema {
    font-style: italic;
    color: var(--text-color-dark);
    margin-top: 6px;
    font-size: 1.1em;
    max-width: 90%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}


/* Image Upload for Orders */
.image-upload-preview {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 15px;
    justify-content: center;
    border: 1px dashed rgba(255,255,255,0.2);
    padding: 10px;
    border-radius: 10px;
    min-height: 80px;
    align-items: center;
    background-color: rgba(44, 44, 74, 0.4);
}

.image-upload-preview img {
    max-width: 90px;
    max-height: 90px;
    object-fit: cover;
    border-radius: 8px;
    border: 1px solid rgba(255,255,255,0.2);
    box-shadow: 0 0 10px rgba(0,0,0,0.2);
}

.image-upload-input-group {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 10px 0;
}
.image-upload-input-group input[type="file"] {
    flex-grow: 1;
    padding: 10px;
    border: 1px solid rgba(41, 121, 255, 0.5);
    background-color: rgba(44, 44, 74, 0.5);
    color: var(--text-color-light);
}
.image-upload-input-group button {
    margin: 0;
    padding: 10px 18px;
    font-size: 0.9em;
    background-color: var(--secondary-color);
    color: var(--background-dark);
    width: auto;
    max-width: none;
}
.image-upload-input-group button:hover {
    background-color: var(--secondary-dark);
}

.pedido-imagen {
    max-width: 150px;
    height: auto;
    border-radius: 8px;
    margin-top: 15px;
    margin-bottom: 15px;
    box-shadow: 0 0 15px rgba(0,230,118,0.2);
    border: 1px solid rgba(0,230,118,0.4);
}

/* Floating Donate Button - REMOVED, now part of utilities screen */
/*
#btn-floating-donar {
    position: fixed;
    bottom: 25px;
    right: 25px;
    z-index: 1001;
    padding: 16px 25px;
    font-size: 1.1em;
    border-radius: 50px;
    background: linear-gradient(45deg, var(--accent-color) 0%, #2979ff 100%);
    color: white;
    box-shadow: 0 5px 20px rgba(0,0,0,0.4), 0 0 15px var(--accent-color);
    transition: all 0.3s ease;
    border: none;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 8px;
    text-transform: uppercase;
}

#btn-floating-donar:hover {
    transform: translateY(-4px) scale(1.06);
    box-shadow: 0 8px 25px rgba(0,0,0,0.5), 0 0 25px var(--accent-color);
    background-position: right center;
}
#btn-floating-donar:active {
    transform: translateY(0) scale(0.98);
}
*/

/* Google Maps Modal Specific Styles */
#modal-google-map .modal {
    max-width: 800px;
    width: 95%;
    max-height: 90vh;
    padding: 20px;
}

#map {
    width: 100%;
    height: 400px; /* Fixed height for the map */
    background-color: #333;
    border-radius: 10px;
    margin-top: 20px;
    border: 1px solid var(--secondary-color);
    box-shadow: inset 0 0 10px rgba(41, 121, 255, 0.2);
}

/* Specific styles for the Donation Modal to make it smaller */
#modal-donar .modal {
    max-width: 400px; /* Reduced max-width */
    max-height: 70vh; /* Reduced max-height */
    overflow-y: auto; /* Enable scrolling if content overflows */
    padding: 25px 30px; /* Slightly reduced padding */
}
#modal-donar ul {
    list-style: none; /* Remove bullet points */
    padding: 0;
    margin: 15px 0;
    text-align: center;
}
#modal-donar li {
    background-color: rgba(0, 230, 118, 0.1); /* Light green background */
    border: 1px solid rgba(0, 230, 118, 0.3);
    padding: 8px 15px;
    margin-bottom: 8px;
    border-radius: 8px;
    font-size: 0.95em;
    color: var(--text-color-light);
}


/* Responsive */
@media (max-width: 768px) {
    body {
        padding-top: 30px;
    }
    h1 {
        font-size: 2.5em;
        margin-bottom: 30px;
        letter-spacing: 0.08em;
    }
    h2 {
        font-size: 1.8em;
    }
    h3 {
        font-size: 1.3em;
    }
    .pantalla {
        padding: 25px 30px;
        width: 95%;
        max-width: none;
        margin-bottom: 30px;
        border-radius: 12px;
    }
    button {
        padding: 12px 22px;
        font-size: 0.9em;
        /* margin: 8px 6px; Removed, handled by .button-section gap */
    }
    input, textarea, select {
        font-size: 0.9em;
        padding: 12px;
    }
    .direccion-input-group {
        flex-direction: column;
        align-items: stretch;
        gap: 8px;
    }
    .direccion-input-group button {
        width: 100%;
        padding: 10px;
    }
    #chat-input-group, #friend-chat-input-group {
        flex-direction: column;
        align-items: stretch;
        gap: 8px;
    }
    #chat-input-group input, #friend-chat-input-group input {
        flex-grow: 1;
        margin: 0;
    }
    #chat-input-group button, #friend-chat-input-group button {
        width: 100%;
    }
    .chat-message {
        max-width: 98%;
        font-size: 0.88em;
    }
    .modal {
        padding: 25px 30px;
        border-radius: 12px;
    }
    .modal-buttons {
        flex-direction: column;
        align-items: stretch;
        gap: 8px;
    }
    .modal-buttons button {
        width: 100%;
    }
    .friend-request, .friend-item {
        flex-direction: column;
        align-items: flex-start;
        gap: 10px;
    }
    .friend-request div, .friend-item div {
        width: 100%;
        justify-content: center;
        flex-wrap: wrap;
    }
    .friend-request button, .friend-item button {
        flex-grow: 1;
        min-width: unset;
    }
    /* Floating donate button removed from here */
    /* #btn-floating-donar {
        bottom: 20px;
        padding: 14px 22px;
        font-size: 1.0em;
    }
    #btn-floating-donar {
        right: 20px;
    } */

    .creditos, .version-info {
        font-size: 0.7em;
        bottom: 10px;
    }
    .creditos { right: 15px; }
    .version-info { left: 15px; }

    #map {
        height: 300px;
    }

    /* Responsive adjustments for Donation Modal */
    #modal-donar .modal {
        max-width: 90%; /* Even smaller on mobile */
        padding: 20px;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: 2em;
        margin-bottom: 25px;
    }
    h2 {
        font-size: 1.5em;
    }
    h3 {
        font-size: 1.1em;
    }
    .pantalla {
        padding: 20px 20px;
        border-radius: 10px;
    }
    button {
        padding: 10px 18px;
        font-size: 0.8em;
    }
    input, textarea, select {
        padding: 10px;
        font-size: 0.85em;
    }
    .modal {
        padding: 20px 25px;
        border-radius: 10px;
    }
    .chat-message {
        font-size: 0.8em;
    }
    /* Floating donate button removed from here */
    /* #btn-floating-donar {
        bottom: 15px;
        padding: 12px 18px;
        font-size: 0.9em;
    }
    #btn-floating-donar {
        right: 15px;
    } */
    .creditos, .version-info {
        font-size: 0.65em;
        bottom: 5px;
    }
    #map {
        height: 250px;
    }
}
</style>
</head>
<body>

<h1><span style="font-size: 0.8em;">🚀</span> ChambAPP</h1>
<div id="toast"><span id="toast-icon"></span><span id="toast-message"></span></div>

<div id="login-register" class="visible pantalla">
<h2>🔐 Zona de Acceso</h2>
<input type="text" id="reg-usuario" placeholder="Nombre de usuario" autocomplete="username" />
<input type="password" id="reg-password" placeholder="Contraseña (mín. 6 caracteres, mayús, minús, número)" autocomplete="current-password" />
<div style="text-align: left; margin-top: 15px; margin-bottom: 10px;">
    <input type="checkbox" id="consent-checkbox" />
    <label for="consent-checkbox" style="font-size: 0.9em; color: var(--text-color-dark);">Acepto los <a href="#" id="view-terms" style="color: var(--secondary-color); text-decoration: underline;">términos y condiciones</a> y entiendo el uso de mi ubicación para los servicios de la app.</label>
</div>
<div class="button-section">
    <button id="btn-registrar">📝 Registrarse</button>
    <button id="btn-login">🔑 Iniciar Sesión</button>
</div>
</div>

<div id="menu-principal" class="pantalla">
<div class="saludo" id="saludoUsuario"></div>
<h2>🏠 Menú Principal</h2>
<div class="button-section">
    <button id="btn-mis-pedidos-y-articulos">📦 Mis Pedidos y Artículos</button>
    <button id="btn-explorar-pedidos">🛒 Explorar Pedidos (Solicitudes)</button>
    <button id="btn-explorar-propuestas">🛍️ Explorar Artículos (Ventas)</button>
    <button id="btn-ver-perfil">👤 Mi Perfil</button>
    <button id="btn-utilidades">⚙️ Utilidades y Más</button>
</div>
<div class="button-section bottom-section">
    <button id="btn-cerrar-sesion">🚪 Cerrar Sesion</button>
</div>
</div>

<!-- NUEVA ZONA: MIS PEDIDOS Y ARTÍCULOS -->
<div id="mis-pedidos-y-articulos-screen" class="pantalla">
    <h2>📦 Mis Pedidos y Artículos</h2>
    <div class="button-section">
        <button id="btn-crear-pedido">📝 Crear Nuevo Pedido (Solicitud)</button>
        <button id="btn-proponer-articulo">✨ Proponer Nuevo Artículo (Venta)</button>
    </div>
    <div class="button-section">
        <button id="btn-ver-mis-pedidos">🛒 Ver Mis Pedidos (Solicitudes)</button>
        <button id="btn-ver-mis-propuestas">🛍️ Ver Mis Artículos (Ventas)</button>
    </div>
    <div class="button-section bottom-section">
        <button id="btn-volver-mis-pedidos-y-articulos">⬅️ Volver al Menú Principal</button>
    </div>
</div>

<!-- NUEVA ZONA: UTILIDADES Y MÁS -->
<div id="utilidades-screen" class="pantalla">
    <h2>⚙️ Utilidades y Más</h2>
    <div class="button-section">
        <button id="btn-show-on-google-maps">🗺️ Mostrar Mi Ubicación en Mapa</button>
        <button id="btn-donar-utilidades">💖 Donar a ChambAPP</button>
        <button id="btn-view-owner-profile">👑 Ver Perfil del Propietario</button>
    </div>
    <div class="button-section bottom-section">
        <button id="btn-volver-utilidades">⬅️ Volver al Menú Principal</button>
    </div>
</div>


<!-- ZONA DE CREACIÓN: SELECCIÓN DE CATEGORÍA -->
<div id="seleccionar-categoria" class="pantalla">
    <h2>📦 Crear Pedido (Solicitud) - Elegir Categoría</h2>
    <div class="button-section">
        <button class="btn-seleccionar-categoria" data-categoria="Ropa">👕 Ropa</button>
        <button class="btn-seleccionar-categoria" data-categoria="Comida Rápida">🍔 Comida Rápida</button>
        <button class="btn-seleccionar-categoria" data-categoria="Electrónica">💻 Electrónica</button>
        <button class="btn-seleccionar-categoria" data-categoria="Servicios">🔧 Servicios</button>
        <button class="btn-seleccionar-categoria" data-categoria="Otros">📦 Otros</button>
    </div>
    <div class="button-section bottom-section">
        <button id="btn-volver-seleccion-categoria">⬅️ Volver a Mis Pedidos y Artículos</button>
    </div>
</div>

<!-- ZONA DE CREACIÓN: CREAR/EDITAR PEDIDO/PROPUESTA -->
<div id="crear-editar-pedido" class="pantalla">
<h2 id="crear-editar-pedido-titulo">📦 Crear un pedido</h2>
<!-- Hidden input to determine order type -->
<input type="hidden" id="inputOrderType" value="request" />

<!-- Input fields for order details -->
<input id="inputNombre" placeholder="Nombre del artículo" />
<input id="inputDescripcion" placeholder="Descripción" />
<input id="inputCantidad" type="text" placeholder="Cantidad (ej. 10 unidades, 2 docenas, 5kg)" />
<input id="inputPrecio" type="number" step="0.01" placeholder="Precio total (S/)" />

<!-- Conditional fields for clothing items -->
<div style="margin-top: 15px; margin-bottom: 10px; text-align: left;">
    <input type="checkbox" id="isRopaCheckbox" />
    <label for="isRopaCheckbox" style="font-weight: 500; color: var(--text-color-dark);">¿Es un artículo de ropa?</label>
</div>

<div id="ropaFields" style="display: none;">
    <select id="inputTalla" style="margin-top: 0;">
        <option value="">Selecciona la Talla</option>
        <option value="XS">XS</option>
        <option value="S">S</option>
        <option value="M">M</option>
        <option value="L">L</option>
        <option value="XL">XL</option>
        <option value="XXL">XXL</option>
        <option value="Única">Única</option>
        <option value="No aplica">No aplica</option>
    </select>
    <select id="inputGenero">
        <option value="">Selecciona el Género</option>
        <option value="Hombre">Hombre</option>
        <option value="Mujer">Mujer</option>
        <option value="Unisex">Unisex</option>
        <option value="Niño/a">Niño/a</option>
        <option value="No aplica">No aplica</option>
    </select>
</div>

<!-- Image upload section -->
<div class="image-upload-input-group">
    <input type="file" id="inputImagenArticulo" accept="image/*" />
    <button id="btn-upload-image">🖼️ Subir Imagen</button>
</div>
<div id="previewImagenArticulo" class="image-upload-preview">
    <p style="color: var(--text-color-dark); font-style: italic;">Sin imagen seleccionada</p>
</div>

<!-- Payment method selection -->
<select id="inputMetodoPago">
    <option value="">Selecciona Método de Pago Preferido</option>
    <option value="Efectivo">Efectivo</option>
    <option value="BCP">Transferencia Bancaria (BCP)</option>
    <option value="Yape">Yape</option>
    <option value="Plin">Plin</option>
    <option value="Otros">Otros</option>
</select>

<!-- Delivery address and geolocation -->
<div class="direccion-input-group">
    <input id="inputDireccion" placeholder="Dirección de entrega (ej. Lat: -12.0000, Lng: -77.0000)" />
    <button id="btn-autocompletar-direccion">📍 Usar mi ubicación actual</button>
</div>

<div class="button-section">
    <button id="btn-crear-pedido-solicitante">Crear</button>
</div>
<div class="button-section bottom-section">
    <button id="btn-volver-crear-editar">⬅️ Volver a Mis Pedidos y Artículos</button>
</div>
</div>

<!-- ZONA DE EXPLORACIÓN: PEDIDOS SOLICITADOS -->
<div id="comprador" class="pantalla">
<h2>🛒 Pedidos Solicitados Disponibles</h2>
<div class="button-section top-section">
    <button id="toggleOcultosBtn" class="btn-ocultar-pedido">🔄 Mostrar Pedidos Ocultos</button>
</div>
<div id="listaPedidos"></div>
<div class="button-section bottom-section">
    <button id="btn-volver-comprador">⬅️ Volver al Menú Principal</button>
</div>
</div>

<!-- ZONA DE EXPLORACIÓN: CATÁLOGO DE ARTÍCULOS PROPUESTOS -->
<div id="catalogo-propuestas" class="pantalla">
    <h2>🛍️ Artículos Propuestos</h2>
    <div class="button-section top-section">
        <button id="toggleOcultosBtnPropuestas" class="btn-ocultar-pedido">🔄 Mostrar Artículos Ocultos</button>
    </div>
    <div id="listaPropuestas"></div>
    <div class="button-section bottom-section">
        <button id="btn-volver-propuestas">⬅️ Volver al Menú Principal</button>
    </div>
</div>

<!-- ZONA DE PERFIL -->
<div id="perfil" class="pantalla">
<h2>👤 Tu Perfil</h2>
<div id="detallePerfil">
    <div id="perfil-header">
        <input type="file" id="inputPerfilFoto" accept="image/*" style="display: none;" />
        <div id="perfil-foto-container">
            <img id="perfil-foto" src="https://via.placeholder.com/120/007bff/ffffff?text=Perfil" alt="" />
        </div>
        <h3 id="perfilUsernameDisplay"></h3>
        <p id="perfilLema"></p>
        <span id="perfilRankBadge" class="rank-badge"></span>
    </div>

<div class="perfil-info-item">
<label for="inputLema">Mi Lema:</label>
<input type="text" id="inputLema" placeholder="Un lema corto sobre ti" maxlength="50" />
</div>
<div class="perfil-info-item">
<label for="perfilDescripcion">Mi Descripción:</label>
<textarea id="perfilDescripcion" placeholder="Escribe algo sobre ti..."></textarea>
</div>
<div class="perfil-info-item">
<input type="checkbox" id="ocultarDireccionCheckbox" />
<label for="ocultarDireccionCheckbox">Ocultar mi dirección en pedidos</label>
</div>
<p id="perfilCalificacion"><b>Calificación:</b> <span id="rating-value-display">No calificado aún</span></p>
<p id="perfilUbicacion"><b>Mi ubicación:</b> No disponible <button id="btn-actualizar-ubicacion">Actualizar mi ubicación</button></p>

<div class="button-section">
    <button id="btn-guardar-perfil">💾 Guardar Cambios del Perfil</button>
</div>

<div id="studentBenefits" style="display:none;" class="button-section">
<p style="font-style: italic; color: var(--rank-student-color);">✨ Como estudiante, disfrutas de un 10% de descuento en tus ofertas.</p>
<button id="btn-obtener-codigo-estudiante">🎓 Obtener Código Estudiante</button>
</div>
<div id="donorBenefits" style="display:none;" class="button-section">
<p style="font-style: italic; color: var(--rank-donor-color);">💖 ¡Gracias por tu generosidad! Tu apoyo hace que ChambAPP sea posible.</p>
</div>
<div id="creatorBenefits" style="display:none;" class="button-section">
<p style="font-style: italic; color: var(--rank-creator-color);">🌟 ¡Eres un creador increíble en nuestra comunidad!</p>
</div>

<h3>Tus Pedidos y Propuestas:</h3>
<div id="listaTusPedidos"></div>

<h3>Tus Amigos:</h3>
<div id="listaAmigos"></div>
<div class="button-section">
    <button id="btn-show-friends">👥 Ver Amigos</button>
</div>

<h3>Solicitudes de Amistad Recibidas:</h3>
<div id="solicitudesAmistadRecibidas"></div>
</div>
<div class="button-section bottom-section">
    <button id="btn-volver-perfil">⬅️ Volver al Menú Principal</button>
</div>
</div>

<!-- MODALES (Zonas Extra) -->

<div id="modal-negociacion" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-negociacion')">✖️</button>
<h3 id="modal-negociacion-titulo">💬 Negociación</h3>
<p id="modal-texto"></p>
<div id="historial-negociacion"></div>
<input id="modal-input-precio" type="number" step="0.01" placeholder="Ingresa tu oferta (S/)" style="display:none" />
<div class="modal-buttons">
<button id="btn-aceptar-oferta" class="btn-accept">Aceptar</button>
<button id="btn-rechazar-oferta" class="btn-reject">Rechazar</button>
<button id="btn-contraofertar" class="btn-counter">Contraoferta</button>
<button id="btn-cancelar-negociacion" class="btn-ocultar-pedido">Cancelar</button>
</div>
</div>
</div>

<div id="modal-calificacion" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-calificacion')">✖️</button>
<h3>⭐ Calificar Pedido</h3>
<p id="calificar-texto">Califica tu experiencia con <span id="calificar-usuario-target"></span>:</p>
<input type="number" id="input-calificacion" min="1" max="5" placeholder="Puntuación (1-5)" />
<textarea id="input-comentario-calificacion" placeholder="Comentario (opcional)" rows="3"></textarea>
<div class="modal-buttons">
<button id="btn-enviar-calificacion">Enviar Calificación</button>
<button id="btn-cancelar-calificacion" class="btn-reject">Cancelar</button>
</div>
</div>
</div>

<div id="modal-chat" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-chat')">✖️</button>
<h3>💬 Chat del Pedido</h3>
<div id="chat-messages"></div>
<div id="chat-input-group">
<input type="text" id="chat-message-input" placeholder="Escribe tu mensaje..." />
<button id="btn-enviar-mensaje">Enviar</button>
</div>
<div class="modal-buttons">
<button id="btn-cerrar-chat" class="btn-ocultar-pedido">Cerrar Chat</button>
</div>
</div>
</div>

<div id="modal-friend-chat" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-friend-chat')">✖️</button>
<h3>💬 Chat con Amigo</h3>
<div id="friend-chat-messages"></div>
<div id="friend-chat-input-group">
<input type="text" id="friend-chat-message-input" placeholder="Escribe tu mensaje..." />
<button id="btn-enviar-friend-message">Enviar</button>
</div>
</div>
</div>

<div id="modal-reportar" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-reportar')">✖️</button>
<h3>🚨 Reportar Usuario</h3>
<p>Estás a punto de reportar a <strong id="reportar-username-target"></strong>.</p>
<textarea id="input-razon-reporte" placeholder="Razón del reporte (obligatorio)" rows="4"></textarea>
<div class="modal-buttons">
<button id="btn-enviar-reporte" class="btn-danger">Enviar Reporte</button>
<button id="btn-cancelar-reporte" class="btn-ocultar-pedido">Cancelar</button>
</div>
</div>
</div>

<div id="modal-donar" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-donar')">✖️</button>
<h3>💖 Donar a ChambAPP</h3>
<p>¡Tu donación nos ayuda a mantener ChambAPP funcionando y mejorando!</p>
<input type="number" id="input-monto-donacion" min="1" step="0.01" placeholder="Monto a donar (S/)" />
<p>Métodos de pago:</p>
<ul>
<li>Yape: [Número de Yape]</li>
<li>Plin: [Número de Plin]</li>
<li>BCP: [Número de cuenta BCP]</li>
</ul>
<p style="font-size: 0.9em; font-style: italic;">Por favor, realiza la transferencia y luego haz click en "Confirmar Donación".</p>
<div class="modal-buttons">
<button id="btn-confirmar-donacion" class="btn-accept">Confirmar Donación</button>
<button id="btn-cancelar-donacion" class="btn-reject">Cancelar</button>
</div>
</div>
</div>

<div id="modal-student-code" class="modal-overlay">
<div class="modal">
<button class="close-btn" onclick="hideModal('modal-student-code')">✖️</button>
<h3>🎓 Código de Estudiante</h3>
<p>Ingresa tu código de estudiante para obtener beneficios:</p>
<input type="text" id="input-student-code" placeholder="Código de estudiante" />
<div class="modal-buttons">
<button id="btn-submit-student-code" class="btn-accept">Enviar Código</button>
<button id="btn-cancel-student-code" class="btn-reject">Cancelar</button>
</div>
</div>
</div>

<!-- Modal para perfil del propietario -->
<div id="modal-owner-profile" class="modal-overlay">
    <div class="modal">
        <button class="close-btn" onclick="hideModal('modal-owner-profile')">✖️</button>
        <div id="owner-perfil-header" style="display: flex; flex-direction: column; align-items: center; margin-bottom: 20px;">
            <img id="owner-profile-photo" src="" alt="" style="width: 120px; height: 120px; border-radius: 50%; object-fit: cover; margin-bottom: 15px; border: 3px solid var(--primary-color); box-shadow: 0 0 15px var(--primary-color);" onerror="this.src='https://placehold.co/120x120/dc3545/ffffff?text=Owner'">
            <h3 id="owner-profile-username-display" style="margin-top: 0;"></h3>
            <p id="owner-profile-lema" style="font-style: italic; color: var(--text-color-dark); margin-top: 6px; font-size: 1.1em;"></p>
            <span id="owner-rank-badge" class="rank-badge"></span>
        </div>
        <p id="owner-profile-description"></p>
        <p id="owner-profile-rating"><b>Calificación:</b> <span id="owner-profile-rating-value"></span></p>
        <div class="modal-buttons">
            <button onclick="hideModal('modal-owner-profile')" class="btn-ocultar-pedido">Cerrar</button>
        </div>
    </div>
</div>

<!-- Modal para Google Maps -->
<div id="modal-google-map" class="modal-overlay">
    <div class="modal">
        <button class="close-btn" onclick="hideModal('modal-google-map')">✖️</button>
        <h3>🗺️ Ubicación en el Mapa</h3>
        <div id="map"></div>
        <div class="modal-buttons">
            <button onclick="hideModal('modal-google-map')" class="btn-ocultar-pedido">Cerrar Mapa</button>
        </div>
    </div>
</div>

<!-- Modal para confirmación de cierre de sesión -->
<div id="modal-logout-confirm" class="modal-overlay">
    <div class="modal">
        <button class="close-btn" onclick="hideModal('modal-logout-confirm')">✖️</button>
        <h3>🚪 Confirmar Salida</h3>
        <p>¿Estás seguro de que quieres cerrar tu sesión?</p>
        <div class="modal-buttons">
            <button id="btn-confirm-logout" class="btn-danger">Sí, cerrar sesión</button>
            <button onclick="hideModal('modal-logout-confirm')" class="btn-ocultar-pedido">Cancelar</button>
        </div>
    </div>
</div>

<div class="creditos">© 2024 ChambAPP. Desarrollado por tus amigos de la universidad.</div>
<div class="version-info">Version 0.04 Alpha</div>

<script>
    // =========================================================================
    // 1. Global Variables and Constants
    // =========================================================================

    // Application data (simulating a local database with localStorage)
    let users = JSON.parse(localStorage.getItem('users')) || {};
    let currentUser = JSON.parse(sessionStorage.getItem('currentUser'));
    let orders = JSON.parse(localStorage.getItem('orders')) || [];
    let friendRequests = JSON.parse(localStorage.getItem('friendRequests')) || {}; // {targetUser: [requester1, requester2]}
    let friends = JSON.parse(localStorage.getItem('friends')) || {}; // {user1: [friend1, friend2]}
    let messages = JSON.parse(localStorage.getItem('messages')) || {}; // {chatId: [{sender, message, timestamp}]}
    let reports = JSON.parse(localStorage.getItem('reports')) || [];

    // Owner user credentials
    const OWNER_USERNAME = "OWNER";
    const OWNER_PASSWORD = "Owner12152";

    // Variables for Google Maps integration
    let map;
    let mapMarker;
    const GOOGLE_MAPS_API_KEY = 'YOUR_GOOGLE_MAPS_API_KEY'; // !!! REPLACE WITH YOUR ACTUAL GOOGLE MAPS API KEY !!!

    // Global variable for the article image being created
    let currentArticleImageBase64 = null;

    // State to control visibility of hidden orders
    let showingHiddenOrders = false;
    let showingHiddenProposedOrders = false; // New state for proposed orders

    // Variables for order rating
    let currentRatingOrderId = null;
    let currentRatingTargetUser = null;
    let isRatingSolicitante = false;

    // Variables for chat
    let currentChatOrderId = null;
    let currentFriendChatUser = null;
    let currentUserToReport = null; // Added for reporting functionality


    // =========================================================================
    // 2. DOM Element References (HTML)
    // =========================================================================

    // Main screens
    const loginRegisterScreen = document.getElementById('login-register');
    const menuPrincipalScreen = document.getElementById('menu-principal');
    const misPedidosYArticulosScreen = document.getElementById('mis-pedidos-y-articulos-screen'); // NEW
    const utilidadesScreen = document.getElementById('utilidades-screen'); // NEW
    const seleccionarCategoriaScreen = document.getElementById('seleccionar-categoria');
    const crearEditarPedidoScreen = document.getElementById('crear-editar-pedido');
    const compradorScreen = document.getElementById('comprador');
    const catalogoPropuestasScreen = document.getElementById('catalogo-propuestas');
    const perfilScreen = document.getElementById('perfil');

    // Login/Register screen elements
    const regUsuarioInput = document.getElementById('reg-usuario');
    const regPasswordInput = document.getElementById('reg-password');
    const consentCheckbox = document.getElementById('consent-checkbox');
    const btnRegistrar = document.getElementById('btn-registrar');
    const btnLogin = document.getElementById('btn-login');

    // Main Menu elements
    const saludoUsuario = document.getElementById('saludoUsuario');
    const btnMisPedidosYArticulos = document.getElementById('btn-mis-pedidos-y-articulos'); // NEW
    const btnExplorarPedidos = document.getElementById('btn-explorar-pedidos'); // Renamed from btn-ver-pedidos
    const btnExplorarPropuestas = document.getElementById('btn-explorar-propuestas'); // Renamed from btn-ver-propuestas
    const btnVerPerfil = document.getElementById('btn-ver-perfil');
    const btnUtilidades = document.getElementById('btn-utilidades'); // NEW
    const btnCerrarSesion = document.getElementById('btn-cerrar-sesion');

    // Mis Pedidos y Artículos screen elements (NEW)
    const btnCrearPedido = document.getElementById('btn-crear-pedido');
    const btnProponerArticulo = document.getElementById('btn-proponer-articulo');
    const btnVerMisPedidos = document.getElementById('btn-ver-mis-pedidos'); // NEW
    const btnVerMisPropuestas = document.getElementById('btn-ver-mis-propuestas'); // NEW
    const btnVolverMisPedidosYArticulos = document.getElementById('btn-volver-mis-pedidos-y-articulos'); // NEW

    // Utilidades screen elements (NEW)
    const btnShowOnGoogleMaps = document.getElementById('btn-show-on-google-maps');
    const btnDonarUtilidades = document.getElementById('btn-donar-utilidades'); // Renamed from btn-floating-donar
    const btnViewOwnerProfile = document.getElementById('btn-view-owner-profile');
    const btnVolverUtilidades = document.getElementById('btn-volver-utilidades'); // NEW

    // Category Selection screen elements
    const btnSeleccionarCategoria = document.querySelectorAll('.btn-seleccionar-categoria');
    const btnVolverSeleccionCategoria = document.getElementById('btn-volver-seleccion-categoria');

    // Create/Edit Order screen elements
    const crearEditarPedidoTitulo = document.getElementById('crear-editar-pedido-titulo');
    const inputOrderType = document.getElementById('inputOrderType');
    const inputNombre = document.getElementById('inputNombre');
    const inputDescripcion = document.getElementById('inputDescripcion');
    const inputCantidad = document.getElementById('inputCantidad');
    const inputPrecio = document.getElementById('inputPrecio');
    const inputMetodoPago = document.getElementById('inputMetodoPago');
    const inputDireccion = document.getElementById('inputDireccion');
    const btnCrearPedidoSolicitante = document.getElementById('btn-crear-pedido-solicitante');
    const btnVolverCrearEditar = document.getElementById('btn-volver-crear-editar');
    const isRopaCheckbox = document.getElementById('isRopaCheckbox');
    const ropaFields = document.getElementById('ropaFields');
    const inputTalla = document.getElementById('inputTalla');
    const inputGenero = document.getElementById('inputGenero');
    const btnAutocompletarDireccion = document.getElementById('btn-autocompletar-direccion');
    const inputImagenArticulo = document.getElementById('inputImagenArticulo');
    const btnUploadImage = document.getElementById('btn-upload-image');
    const previewImagenArticulo = document.getElementById('previewImagenArticulo');

    // Buyer screen elements (View Requested Orders)
    const listaPedidos = document.getElementById('listaPedidos');
    const btnVolverComprador = document.getElementById('btn-volver-comprador');
    const toggleOcultosBtn = document.getElementById('toggleOcultosBtn');

    // Proposed Catalog screen elements
    const listaPropuestas = document.getElementById('listaPropuestas');
    const btnVolverPropuestas = document.getElementById('btn-volver-propuestas');
    const toggleOcultosBtnPropuestas = document.getElementById('toggleOcultosBtnPropuestas'); // New button for proposed orders

    // Profile screen elements
    const perfilFotoContainer = document.getElementById('perfil-foto-container');
    const inputPerfilFoto = document.getElementById('inputPerfilFoto');
    const perfilFoto = document.getElementById('perfil-foto');
    const perfilUsernameDisplay = document.getElementById('perfilUsernameDisplay');
    const perfilLema = document.getElementById('perfilLema');
    const inputLema = document.getElementById('inputLema');
    const perfilRankBadge = document.getElementById('perfilRankBadge');
    const perfilCalificacion = document.getElementById('perfilCalificacion');
    const ratingValueDisplay = document.getElementById('rating-value-display');
    const perfilDescripcion = document.getElementById('perfilDescripcion');
    const ocultarDireccionCheckbox = document.getElementById('ocultarDireccionCheckbox');
    const perfilUbicacion = document.getElementById('perfilUbicacion');
    const btnActualizarUbicacion = document.getElementById('btn-actualizar-ubicacion');
    const btnGuardarPerfil = document.getElementById('btn-guardar-perfil');
    const btnVolverPerfil = document.getElementById('btn-volver-perfil');
    const listaTusPedidos = document.getElementById('listaTusPedidos');
    const listaAmigos = document.getElementById('listaAmigos');
    const btnShowFriends = document.getElementById('btn-show-friends');
    const solicitudesAmistadRecibidas = document.getElementById('solicitudesAmistadRecibidas');

    // Modal elements
    const modalNegociacion = document.getElementById('modal-negociacion');
    const modalNegociacionTitulo = document.getElementById('modal-negociacion-titulo');
    const modalTexto = document.getElementById('modal-texto');
    const historialNegociacion = document.getElementById('historial-negociacion');
    const modalInputPrecio = document.getElementById('modal-input-precio');
    const btnAceptarOferta = document.getElementById('btn-aceptar-oferta');
    const btnRechazarOferta = document.getElementById('btn-rechazar-oferta');
    const btnContraofertar = document.getElementById('btn-contraofertar');
    const btnCancelarNegociacion = document.getElementById('btn-cancelar-negociacion');

    const modalCalificacion = document.getElementById('modal-calificacion');
    const calificarTexto = document.getElementById('calificar-texto');
    const calificarUsuarioTarget = document.getElementById('calificar-usuario-target');
    const inputCalificacion = document.getElementById('input-calificacion');
    const inputComentarioCalificacion = document.getElementById('input-comentario-calificacion');
    const btnEnviarCalificacion = document.getElementById('btn-enviar-calificacion');
    const btnCancelarCalificacion = document.getElementById('btn-cancelar-calificacion');

    const modalChat = document.getElementById('modal-chat');
    const chatTitulo = document.getElementById('chat-titulo');
    const chatMessages = document.getElementById('chat-messages');
    const chatMessageInput = document.getElementById('chat-message-input');
    const btnEnviarMensaje = document.getElementById('btn-enviar-mensaje');
    const btnCerrarChat = document.getElementById('btn-cerrar-chat');

    const modalFriendChat = document.getElementById('modal-friend-chat');
    const friendChatTitulo = document.getElementById('friend-chat-titulo');
    const friendChatMessages = document.getElementById('friend-chat-messages');
    const friendChatMessageInput = document.getElementById('friend-chat-message-input');
    const btnEnviarFriendMessage = document.getElementById('btn-enviar-friend-message');
    const btnCerrarFriendChat = document.getElementById('btn-cerrar-friend-chat');

    const modalReportar = document.getElementById('modal-reportar');
    const reportarUsernameTarget = document.getElementById('reportar-username-target');
    const inputRazonReporte = document.getElementById('input-razon-reporte');
    const btnEnviarReporte = document.getElementById('btn-enviar-reporte');
    const btnCancelarReporte = document.getElementById('btn-cancelar-reporte');

    const modalDonar = document.getElementById('modal-donar');
    const inputMontoDonacion = document.getElementById('input-monto-donacion');
    const btnConfirmarDonacion = document.getElementById('btn-confirmar-donacion');
    const btnCancelarDonacion = document.getElementById('btn-cancelar-donacion');

    const studentBenefitsDiv = document.getElementById('studentBenefits');
    const btnObtenerCodigoEstudiante = document.getElementById('btn-obtener-codigo-estudiante');
    const donorBenefitsDiv = document.getElementById('donorBenefits');
    const creatorBenefitsDiv = document.getElementById('creatorBenefits');
    const modalStudentCode = document.getElementById('modal-student-code');
    const inputStudentCode = document.getElementById('input-student-code');
    const btnSubmitStudentCode = document.getElementById('btn-submit-student-code');
    const btnCancelStudentCode = document.getElementById('btn-cancel-student-code');

    const toastDiv = document.getElementById('toast');
    const toastIcon = document.getElementById('toast-icon');
    const toastMessage = document.getElementById('toast-message');

    // Owner profile modal elements
    const modalOwnerProfile = document.getElementById('modal-owner-profile');
    const ownerProfilePhoto = document.getElementById('owner-profile-photo');
    const ownerProfileUsernameDisplay = document.getElementById('owner-profile-username-display');
    const ownerProfileLema = document.getElementById('owner-profile-lema');
    const ownerProfileDescription = document.getElementById('owner-profile-description');
    const ownerRankBadge = document.getElementById('owner-rank-badge');
    const ownerProfileRatingValue = document.getElementById('owner-profile-rating-value');

    // Logout confirmation modal elements
    const modalLogoutConfirm = document.getElementById('modal-logout-confirm');
    const btnConfirmLogout = document.getElementById('btn-confirm-logout');

    // Google Maps modal elements
    const modalGoogleMap = document.getElementById('modal-google-map');
    const mapDiv = document.getElementById('map');


    // =========================================================================
    // 3. Utility and UI Functions
    // =========================================================================

    /**
     * Shows a specific screen and hides all others.
     * @param {HTMLElement} screenToShow - The screen element to make visible.
     */
    function showScreen(screenToShow) {
        console.log(`[ChambAPP Debug] Showing screen: ${screenToShow.id}`);
        const screens = [
            loginRegisterScreen, menuPrincipalScreen, misPedidosYArticulosScreen, utilidadesScreen,
            seleccionarCategoriaScreen, crearEditarPedidoScreen, compradorScreen, catalogoPropuestasScreen,
            perfilScreen
        ];
        screens.forEach(screen => {
            screen.classList.remove('visible');
        });
        screenToShow.classList.add('visible');
    }

    /**
     * Displays a "toast" notification on the screen.
     * @param {string} message - The message to display.
     * @param {string} type - 'success', 'danger', 'warning', or 'info'.
     * @param {string} icon - Emoji or icon character.
     */
    function showToast(message, type = 'info', icon = '') {
        console.log(`[ChambAPP Toast] Type: ${type}, Message: ${message}`);
        toastDiv.className = 'show';
        toastDiv.classList.add(type);
        toastIcon.textContent = icon;
        toastMessage.textContent = message;

        setTimeout(() => {
            toastDiv.classList.remove('show');
            setTimeout(() => {
                toastIcon.textContent = '';
                toastMessage.textContent = '';
            }, 400);
        }, 3000);
    }

    /**
     * Displays a modal (popup window).
     * @param {string} modalId - The ID of the modal to display.
     */
    function showModal(modalId) {
        console.log(`[ChambAPP Debug] Showing modal: ${modalId}`);
        const modalOverlay = document.getElementById(modalId);
        if (modalOverlay) {
            modalOverlay.classList.add('visible');
        }
    }

    /**
     * Hides a modal (popup window).
     * @param {string} modalId - The ID of the modal to hide.
     */
    function hideModal(modalId) {
        console.log(`[ChambAPP Debug] Hiding modal: ${modalId}`);
        const modalOverlay = document.getElementById(modalId);
        if (modalOverlay) {
            modalOverlay.classList.remove('visible');
        }
    }

    /**
     * Creates a default user profile.
     * @param {string} username - The username for the new profile.
     * @returns {object} - The default profile object.
     */
    function createDefaultUserProfile(username) {
        return {
            password: '',
            rank: 'new',
            calificaciones: [],
            description: '',
            location: null, // Location will be stored as {lat, lng}
            hideAddress: false,
            profilePicture: 'https://via.placeholder.com/120/007bff/ffffff?text=Perfil',
            lema: '',
            username: username // Ensure username is in the profile
        };
    }

    /**
     * Calculates the average rating for a user.
     * @param {string} username - The username.
     * @returns {string} - Formatted rating or "Not yet rated".
     */
    function calculateUserRating(username) {
        if (!users[username] || users[username].calificaciones.length === 0) {
            return 'No calificado aún';
        }
        const totalScore = users[username].calificaciones.reduce((sum, c) => sum + c.score, 0);
        const averageScore = (totalScore / users[username].calificaciones.length).toFixed(1);
        return `${averageScore} (${users[username].calificaciones.length} calificaciones)`;
    }


    // =========================================================================
    // 4. Data Persistence Functions (LocalStorage)
    // =========================================================================

    function saveUsers() {
        localStorage.setItem('users', JSON.stringify(users));
        console.log('[ChambAPP Debug] Users saved to localStorage:', users);
    }

    function saveOrders() {
        localStorage.setItem('orders', JSON.stringify(orders));
        console.log('[ChambAPP Debug] Orders saved to localStorage:', orders);
    }

    function saveFriendRequests() {
        localStorage.setItem('friendRequests', JSON.stringify(friendRequests));
        console.log('[ChambAPP Debug] Friend requests saved to localStorage:', friendRequests);
    }

    function saveFriends() {
        localStorage.setItem('friends', JSON.stringify(friends));
        console.log('[ChambAPP Debug] Friends saved to localStorage:', friends);
    }

    function saveMessages() {
        localStorage.setItem('messages', JSON.stringify(messages));
        console.log('[ChambAPP Debug] Messages saved to localStorage:', messages);
    }

    function saveReports() {
        localStorage.setItem('reports', JSON.stringify(reports));
        console.log('[ChambAPP Debug] Reports saved to localStorage:', reports);
    }

    /**
     * Sets the current user and updates the UI.
     * @param {string|null} user - The current username or null if no session.
     */
    function setCurrentUser(user) {
        currentUser = user;
        sessionStorage.setItem('currentUser', JSON.stringify(currentUser));
        console.log('[ChambAPP Debug] Current user set to:', currentUser);
        updateUIForCurrentUser();
    }


    // =========================================================================
    // 5. Authentication and User Management
    // =========================================================================

    /**
     * Registers a new user in the application.
     */
    function register() {
        console.log('[ChambAPP Debug] Register function called.');
        const username = regUsuarioInput.value.trim();
        const password = regPasswordInput.value;
        console.log('[ChambAPP Debug] Register attempt - Username:', username, 'Password length:', password.length);
        console.log('[ChambAPP Debug] Current users object before register:', JSON.parse(localStorage.getItem('users')));


        if (!username || !password) {
            showToast('Por favor, ingresa usuario y contraseña.', 'warning', '⚠️');
            return;
        }

        if (password.length < 6 || !/[A-Z]/.test(password) || !/[a-z]/.test(password) || !/\d/.test(password)) {
            showToast('Contraseña debe tener al menos 6 caracteres, mayúscula, minúscula y número.', 'danger', '❌');
            return;
        }

        if (!consentCheckbox.checked) {
            showToast('Debes aceptar los términos y condiciones para registrarte.', 'danger', '❌');
            return;
        }

        if (users[username]) {
            showToast('El usuario ya existe. Intenta con otro.', 'warning', '⚠️');
            return;
        }

        // Prevent registering with the owner's username
        if (username === OWNER_USERNAME) {
            showToast(`El nombre de usuario "${OWNER_USERNAME}" está reservado.`, 'danger', '❌');
            return;
        }

        const newUserProfile = createDefaultUserProfile(username);
        newUserProfile.password = password;
        users[username] = newUserProfile;

        saveUsers();
        showToast('Registro exitoso. ¡Ahora puedes iniciar sesión!', 'success', '✅');

        setCurrentUser(username);
        navigateToMainMenu(); // Navigate to main menu after registration

        regUsuarioInput.value = '';
        regPasswordInput.value = '';
        consentCheckbox.checked = false;
        console.log('[ChambAPP Debug] Registration successful. Current users object after register:', JSON.parse(localStorage.getItem('users')));
    }

    /**
     * Logs in a user.
     */
    function login() {
        console.log('[ChambAPP Debug] Login function called.');
        const username = regUsuarioInput.value.trim();
        const password = regPasswordInput.value;
        console.log('[ChambAPP Debug] Login attempt - Username:', username, 'Password length:', password.length);
        console.log('[ChambAPP Debug] Current users object before login:', JSON.parse(localStorage.getItem('users')));


        if (!username || !password) {
            showToast('Por favor, ingresa usuario y contraseña.', 'warning', '⚠️');
            return;
        }

        // Special login for the OWNER
        if (username === OWNER_USERNAME && password === OWNER_PASSWORD) {
            setCurrentUser(OWNER_USERNAME);
            showToast(`¡Hola de nuevo, ${OWNER_USERNAME}!`, 'success', '👋');
            navigateToMainMenu(); // Navigate to main menu
            regUsuarioInput.value = '';
            regPasswordInput.value = '';
            console.log('[ChambAPP Debug] Owner login successful.');
            return;
        }

        // Normal user login
        if (users[username] && users[username].password === password) {
            setCurrentUser(username);
            showToast(`¡Hola de nuevo, ${username}!`, 'success', '👋');
            navigateToMainMenu(); // Navigate to main menu
            regUsuarioInput.value = '';
            regPasswordInput.value = '';
            console.log('[ChambAPP Debug] User login successful for:', username);
        } else {
            showToast('Usuario o contraseña incorrectos.', 'danger', '❌');
            console.log('[ChambAPP Debug] Login failed: Incorrect username or password.');
        }
    }

    /**
     * Logs out the current user.
     */
    function logout() {
        console.log('[ChambAPP Debug] Logout function called.');
        setCurrentUser(null);
        showToast('Sesión cerrada. ¡Vuelve pronto!', 'info', '👋');
        hideModal('modal-logout-confirm');
        showLoginRegisterZone(); // Navigate back to login/register
    }

    /**
     * Updates UI elements based on the current user.
     */
    function updateUIForCurrentUser() {
        console.log('[ChambAPP Debug] updateUIForCurrentUser called. CurrentUser:', currentUser);
        if (currentUser) {
            saludoUsuario.textContent = `¡Hola, ${currentUser}!`;
        } else {
            saludoUsuario.textContent = '';
        }
    }


    // =========================================================================
    // 6. Navigation Functions (Zone Management)
    // =========================================================================

    function showLoginRegisterZone() {
        showScreen(loginRegisterScreen);
    }

    function navigateToMainMenu() {
        showScreen(menuPrincipalScreen);
    }

    function navigateToMisPedidosYArticulos() { // NEW
        showScreen(misPedidosYArticulosScreen);
    }

    function navigateToUtilidades() { // NEW
        showScreen(utilidadesScreen);
    }

    function navigateToCreateRequestOrderCategorySelection() {
        inputOrderType.value = 'request';
        crearEditarPedidoTitulo.textContent = '📦 Crear Pedido (Solicitud)';
        showScreen(seleccionarCategoriaScreen);
    }

    function navigateToProposeArticle() {
        inputOrderType.value = 'proposed';
        crearEditarPedidoTitulo.textContent = '✨ Proponer un Artículo (Venta)';
        // Clear form fields when navigating to create/edit order screen
        inputNombre.value = '';
        inputDescripcion.value = '';
        inputCantidad.value = '';
        inputPrecio.value = '';
        inputMetodoPago.value = '';
        inputDireccion.value = '';
        isRopaCheckbox.checked = false;
        ropaFields.style.display = 'none';
        inputTalla.value = '';
        inputGenero.value = '';
        inputImagenArticulo.value = '';
        previewImagenArticulo.innerHTML = '<p style="color: var(--text-color-dark); font-style: italic;">Sin imagen seleccionada</p>';
        currentArticleImageBase64 = null;
        showScreen(crearEditarPedidoScreen);
    }

    function navigateToRequestsCatalog() {
        showScreen(compradorScreen);
        renderOrders();
    }

    function navigateToProposedCatalog() {
        showScreen(catalogoPropuestasScreen);
        renderProposedOrders();
    }

    function navigateToProfile() {
        showScreen(perfilScreen);
        renderPerfil();
    }

    // =========================================================================
    // 7. Order Management
    // =========================================================================

    /**
     * Creates a new order with form data.
     */
    function createOrder() {
        if (!currentUser) {
            showToast('Debes iniciar sesión para crear un pedido.', 'danger', '❌');
            return;
        }

        const nombre = inputNombre.value.trim();
        const descripcion = inputDescripcion.value.trim();
        const cantidad = inputCantidad.value.trim();
        const precio = parseFloat(inputPrecio.value);
        const metodoPago = inputMetodoPago.value;
        const direccion = inputDireccion.value.trim();
        const isRopa = isRopaCheckbox.checked;
        const talla = isRopa ? inputTalla.value : 'No aplica';
        const genero = isRopa ? inputGenero.value : 'No aplica';
        const imageUrl = currentArticleImageBase64;
        const type = inputOrderType.value; // Get the order type from the hidden input

        if (!nombre || !descripcion || !cantidad || isNaN(precio) || precio <= 0 || !metodoPago || !direccion) {
            showToast('Por favor, completa todos los campos obligatorios del pedido.', 'warning', '⚠️');
            return;
        }

        if (isRopa && (!talla || !genero)) {
            showToast('Por favor, selecciona la talla y género para el artículo de ropa.', 'warning', '⚠️');
            return;
        }

        // Try to parse the address if it has Lat: X, Lng: Y format to save the location
        let parsedLocation = null;
        const locationMatch = direccion.match(/Lat:\s*([-\d.]+),\s*Lng:\s*([-\d.]+)/);
        if (locationMatch) {
            parsedLocation = {
                lat: parseFloat(locationMatch[1]),
                lng: parseFloat(locationMatch[2])
            };
        }

        const newOrder = {
            id: Date.now().toString(),
            solicitante: currentUser,
            nombre,
            descripcion,
            cantidad,
            precio,
            metodoPago,
            direccion, // Save the address as entered
            location: parsedLocation, // Save the location object if parsed
            isRopa,
            talla,
            genero,
            imageUrl: imageUrl,
            comprador: null,
            estado: 'abierto',
            oculto: false,
            ofertas: [],
            chat: [],
            calificado: false,
            type: type // Assign the type to the order
        };

        orders.push(newOrder);
        saveOrders();
        showToast('¡Pedido creado con éxito!', 'success', '✅');
        navigateToMisPedidosYArticulos(); // Navigate to new section after creation
        // Clear form
        inputNombre.value = '';
        inputDescripcion.value = '';
        inputCantidad.value = '';
        inputPrecio.value = '';
        inputMetodoPago.value = '';
        inputDireccion.value = '';
        isRopaCheckbox.checked = false;
        ropaFields.style.display = 'none';
        inputTalla.value = '';
        inputGenero.value = '';
        inputImagenArticulo.value = '';
        previewImagenArticulo.innerHTML = '<p style="color: var(--text-color-dark); font-style: italic;">Sin imagen seleccionada</p>';
        currentArticleImageBase64 = null;
    }

    /**
     * Renders the list of 'request' type orders available for the buyer.
     */
    function renderOrders() {
        if (listaPedidos) listaPedidos.innerHTML = '';

        let ordersToDisplay = orders.filter(order => order.solicitante !== currentUser && order.type === 'request');

        if (!showingHiddenOrders) {
            ordersToDisplay = ordersToDisplay.filter(order => !order.oculto);
        }

        if (ordersToDisplay.length === 0) {
            if (listaPedidos) listaPedidos.innerHTML = '<p>No hay pedidos solicitados disponibles en este momento.</p>';
            return;
        }

        ordersToDisplay.forEach(order => {
            const orderDiv = document.createElement('div');
            orderDiv.classList.add('pedido');
            // Add style classes based on negotiation status
            if (order.estado === 'en_negociacion') {
                const lastOffer = order.ofertas[order.ofertas.length - 1];
                if (lastOffer && lastOffer.status === 'pending') {
                     if (lastOffer.user === currentUser || order.solicitante === currentUser) {
                         orderDiv.classList.add('negociacion-pendiente');
                     }
                }
            } else if (order.estado === 'aceptado') {
                orderDiv.classList.add('negociacion-aceptada');
            } else if (order.estado === 'rechazado' || order.estado === 'cancelado') {
                orderDiv.classList.add('negociacion-rechazada');
            }

            let statusBadgeClass = '';
            let statusText = '';
            // Determine text and class for the status badge
            if (order.estado === 'abierto') {
                statusBadgeClass = 'info';
                statusText = 'Abierto';
            } else if (order.estado === 'en_negociacion') {
                statusBadgeClass = 'warning';
                statusText = 'Negociación';
            } else if (order.estado === 'aceptado') {
                statusBadgeClass = 'success';
                statusText = 'Aceptado';
            } else if (order.estado === 'rechazado') {
                statusBadgeClass = 'danger';
                statusText = 'Rechazado';
            } else if (order.estado === 'completado') {
                statusBadgeClass = 'finalizado';
                statusText = 'Completado';
            } else if (order.estado === 'cancelado') {
                statusBadgeClass = 'danger';
                statusText = 'Cancelado';
            }

            const solicitanteInfo = users[order.solicitante];
            // Show hidden address if the requester has configured it
            const solicitanteDisplayAddress = (solicitanteInfo && solicitanteInfo.hideAddress) ? 'Dirección oculta' : order.direccion;

            let ropaDetails = '';
            if (order.isRopa) {
                ropaDetails = `<p><b>Talla:</b> ${order.talla} | <b>Género:</b> ${order.genero}</p>`;
            }

            const itemImage = order.imageUrl ? `<img src="${order.imageUrl}" alt="" class="pedido-imagen">` : '';

            // Logic for add friend button
            const isSolicitante = order.solicitante === currentUser;
            const areFriends = friends[currentUser] && friends[currentUser].includes(order.solicitante);
            const requestSent = friendRequests[order.solicitante] && friendRequests[order.solicitante].includes(currentUser);
            const requestReceived = friendRequests[currentUser] && friendRequests[currentUser].includes(order.solicitante);

            let addFriendButtonHtml = '';
            if (!isSolicitante) {
                if (areFriends) {
                    addFriendButtonHtml = `<span style="font-size:0.9em; color:var(--primary-color);">Amigos</span>`;
                } else if (requestSent) {
                    addFriendButtonHtml = `<span style="font-size:0.9em; color:var(--text-color-dark);">Solicitud enviada</span>`;
                } else if (requestReceived) {
                    addFriendButtonHtml = `<button class="btn-accept-friend-prompt btn-accept" data-requester="${order.solicitante}">🤝 Aceptar Solicitud</button>`;
                } else {
                    addFriendButtonHtml = `<button class="btn-add-friend" data-target-user="${order.solicitante}">➕ Añadir Amigo</button>`;
                }
            }

            // Logic for "View Location" button of the order
            let viewLocationButtonHtml = '';
            const canViewLocation = order.location && (order.estado === 'aceptado' || users[currentUser].rank === 'owner' || (order.solicitante === currentUser && !users[order.solicitante].hideAddress));
            if (canViewLocation) {
                viewLocationButtonHtml = `<button class="btn-mapa" data-order-id="${order.id}" data-location-lat="${order.location.lat}" data-location-lng="${order.location.lng}">Ver Ubicación</button>`;
            }

            orderDiv.innerHTML = `
                <h3>${order.nombre} <span class="status-badge ${statusBadgeClass}">${statusText}</span></h3>
                <p><b>Descripción:</b> ${order.descripcion}</p>
                <p><b>Cantidad:</b> ${order.cantidad}</p>
                <p><b>Precio Sugerido:</b> S/ ${order.precio.toFixed(2)}</p>
                ${ropaDetails}
                ${itemImage}
                <p><b>Método de Pago:</b> ${order.metodoPago}</p>
                <p><b>Dirección:</b> ${solicitanteDisplayAddress}</p>
                <p><b>Solicitante:</b> ${order.solicitante} ${addFriendButtonHtml}</p>
                ${order.oculto ? '<p style="color: grey; font-style: italic;">(Este pedido está oculto)</p>' : ''}
                <div>
                    ${order.estado === 'abierto' || (order.estado === 'en_negociacion' && order.comprador !== currentUser) ?
                    `<button class="btn-ofertar" data-order-id="${order.id}">Hacer Oferta</button>` : ''}
                    ${order.comprador === currentUser && (order.estado === 'en_negociacion' || order.estado === 'aceptado') ?
                    `<button class="btn-chat" data-order-id="${order.id}">Abrir Chat</button>` : ''}
                    ${order.estado === 'aceptado' && order.comprador === currentUser && !order.calificado ?
                    `<button class="btn-calificar-solicitante" data-order-id="${order.id}" data-target-user="${order.solicitante}">Calificar Solicitante</button>` : ''}
                    <button class="btn-reportar" data-target-user="${order.solicitante}">Reportar Usuario</button>
                    ${order.estado === 'abierto' || order.estado === 'en_negociacion' ?
                     `<button class="btn-ocultar-pedido" data-order-id="${order.id}">${order.oculto ? 'Mostrar' : 'Ocultar'} Pedido</button>` : ''}
                     ${viewLocationButtonHtml}
                </div>
            `;
            if (listaPedidos) listaPedidos.appendChild(orderDiv);
        });

        addOrderButtonListeners();
    }

    /**
     * Renders the list of 'proposed' type orders available in the catalog.
     */
    function renderProposedOrders() {
        if (listaPropuestas) listaPropuestas.innerHTML = '';

        let ordersToDisplay = orders.filter(order => order.solicitante !== currentUser && order.type === 'proposed');

        if (!showingHiddenProposedOrders) { // Apply hidden filter to proposed orders as well
            ordersToDisplay = ordersToDisplay.filter(order => !order.oculto);
        }

        if (ordersToDisplay.length === 0) {
            if (listaPropuestas) listaPropuestas.innerHTML = '<p>No hay artículos propuestos disponibles en este momento.</p>';
            return;
        }

        ordersToDisplay.forEach(order => {
            const orderDiv = document.createElement('div');
            orderDiv.classList.add('pedido'); // Reuse existing .pedido style

            let statusBadgeClass = '';
            let statusText = '';
            // Determine text and class for the badge of status
            if (order.estado === 'abierto') {
                statusBadgeClass = 'info';
                statusText = 'Disponible';
            } else if (order.estado === 'en_negociacion') {
                statusBadgeClass = 'warning';
                statusText = 'Negociación';
            } else if (order.estado === 'aceptado') {
                statusBadgeClass = 'success';
                statusText = 'Aceptado';
            } else if (order.estado === 'vendido') { // New status for proposed items
                statusBadgeClass = 'finalizado';
                statusText = 'Vendido';
            } else if (order.estado === 'cancelado') {
                statusBadgeClass = 'danger';
                statusText = 'Cancelado';
            }

            const solicitanteInfo = users[order.solicitante];
            const solicitanteDisplayAddress = (solicitanteInfo && solicitanteInfo.hideAddress) ? 'Dirección oculta' : order.direccion;

            let ropaDetails = '';
            if (order.isRopa) {
                ropaDetails = `<p><b>Talla:</b> ${order.talla} | <b>Género:</b> ${order.genero}</p>`;
            }

            const itemImage = order.imageUrl ? `<img src="${order.imageUrl}" alt="" class="pedido-imagen">` : '';

            const isSolicitante = order.solicitante === currentUser;
            const areFriends = friends[currentUser] && friends[currentUser].includes(order.solicitante);
            const requestSent = friendRequests[order.solicitante] && friendRequests[order.solicitante].includes(currentUser);
            const requestReceived = friendRequests[currentUser] && friendRequests[currentUser].includes(order.solicitante);

            let addFriendButtonHtml = '';
            if (!isSolicitante) {
                if (areFriends) {
                    addFriendButtonHtml = `<span style="font-size:0.9em; color:var(--primary-color);">Amigos</span>`;
                } else if (requestSent) {
                    addFriendButtonHtml = `<span style="font-size:0.9em; color:var(--text-color-dark);">Solicitud enviada</span>`;
                } else if (requestReceived) {
                    addFriendButtonHtml = `<button class="btn-accept-friend-prompt btn-accept" data-requester="${order.solicitante}">🤝 Aceptar Solicitud</button>`;
                } else {
                    addFriendButtonHtml = `<button class="btn-add-friend" data-target-user="${order.solicitante}">➕ Añadir Amigo</button>`;
                }
            }

            let viewLocationButtonHtml = '';
            const canViewLocation = order.location && (order.estado === 'aceptado' || users[currentUser].rank === 'owner' || (order.solicitante === currentUser && !users[order.solicitante].hideAddress));
            if (canViewLocation) {
                viewLocationButtonHtml = `<button class="btn-mapa" data-order-id="${order.id}" data-location-lat="${order.location.lat}" data-location-lng="${order.location.lng}">Ver Ubicación</button>`;
            }

            orderDiv.innerHTML = `
                <h3>${order.nombre} <span class="status-badge ${statusBadgeClass}">${statusText}</span></h3>
                <p><b>Descripción:</b> ${order.descripcion}</p>
                <p><b>Cantidad:</b> ${order.cantidad}</p>
                <p><b>Precio Propuesto:</b> S/ ${order.precio.toFixed(2)}</p>
                ${ropaDetails}
                ${itemImage}
                <p><b>Método de Pago Preferido:</b> ${order.metodoPago}</p>
                <p><b>Ubicación del Artículo:</b> ${solicitanteDisplayAddress}</p>
                <p><b>Proponente:</b> ${order.solicitante} ${addFriendButtonHtml}</p>
                ${order.oculto ? '<p style="color: grey; font-style: italic;">(Este artículo está oculto)</p>' : ''}
                <div>
                    ${order.estado === 'abierto' || (order.estado === 'en_negociacion' && order.comprador !== currentUser) ?
                    `<button class="btn-ofertar" data-order-id="${order.id}">Hacer Oferta</button>` : ''}
                    ${order.comprador === currentUser && (order.estado === 'en_negociacion' || order.estado === 'aceptado') ?
                    `<button class="btn-chat" data-order-id="${order.id}">Abrir Chat</button>` : ''}
                    ${order.estado === 'aceptado' && order.comprador === currentUser && !order.calificado ?
                    `<button class="btn-calificar-solicitante" data-order-id="${order.id}" data-target-user="${order.solicitante}">Calificar Proponente</button>` : ''}
                    <button class="btn-reportar" data-target-user="${order.solicitante}">Reportar Usuario</button>
                    ${order.estado === 'abierto' || order.estado === 'en_negociacion' ?
                     `<button class="btn-ocultar-pedido" data-order-id="${order.id}">${order.oculto ? 'Mostrar' : 'Ocultar'} Artículo</button>` : ''}
                     ${viewLocationButtonHtml}
                </div>
            `;
            if (listaPropuestas) listaPropuestas.appendChild(orderDiv);
        });

        addOrderButtonListeners(); // Re-use listeners for offer, chat, report, hide
    }


    /**
     * Renders the list of orders created by the current user.
     * Now displays both requested orders and proposed items.
     */
    function renderYourOrders() {
        if (listaTusPedidos) listaTusPedidos.innerHTML = '';
        const yourOrders = orders.filter(order => order.solicitante === currentUser);

        if (yourOrders.length === 0) {
            if (listaTusPedidos) listaTusPedidos.innerHTML = '<p>No has creado ningún pedido o propuesto ningún artículo aún.</p>';
            return;
        }

        yourOrders.forEach(order => {
            const orderDiv = document.createElement('div');
            orderDiv.classList.add('pedido');
            // Add style classes based on negotiation status
            if (order.estado === 'en_negociacion') {
                const lastOffer = order.ofertas[order.ofertas.length - 1];
                if (lastOffer && lastOffer.status === 'pending') {
                    orderDiv.classList.add('negociacion-pendiente');
                }
            } else if (order.estado === 'aceptado') {
                orderDiv.classList.add('negociacion-aceptada');
            } else if (order.estado === 'rechazado' || order.estado === 'cancelado') {
                orderDiv.classList.add('negociacion-rechazada');
            }

            let statusBadgeClass = '';
            let statusText = '';
            let orderTypeLabel = order.type === 'request' ? 'Pedido Solicitado' : 'Artículo Propuesto';
            // Determine text and class for the badge of status
            if (order.estado === 'abierto') {
                statusBadgeClass = 'info';
                statusText = order.type === 'request' ? 'Abierto' : 'Disponible';
            } else if (order.estado === 'en_negociacion') {
                statusBadgeClass = 'warning';
                statusText = 'Negociación';
            } else if (order.estado === 'aceptado') {
                statusBadgeClass = 'success';
                statusText = 'Aceptado';
            } else if (order.estado === 'rechazado') {
                statusBadgeClass = 'danger';
                statusText = 'Rechazado';
            } else if (order.estado === 'completado') {
                statusBadgeClass = 'finalizado';
                statusText = 'Completado';
            } else if (order.estado === 'vendido') { // New status for proposed items
                statusBadgeClass = 'finalizado';
                statusText = 'Vendido';
            } else if (order.estado === 'cancelado') {
                statusBadgeClass = 'danger';
                statusText = 'Cancelado';
            }

            let compradorInfo = order.comprador ? `<b>${order.type === 'request' ? 'Comprador' : 'Interesado'}:</b> ${order.comprador}` : '';

            let ropaDetails = '';
            if (order.isRopa) {
                ropaDetails = `<p><b>Talla:</b> ${order.talla} | <b>Género:</b> ${order.genero}</p>`;
            }
            const itemImage = order.imageUrl ? `<img src="${order.imageUrl}" alt="" class="pedido-imagen">` : '';

            // Logic for "View Location" button of the order
            let viewLocationButtonHtml = '';
            const canViewLocation = order.location && (order.estado === 'aceptado' || users[currentUser].rank === 'owner' || (order.solicitante === currentUser && !users[order.solicitante].hideAddress));
            if (canViewLocation) {
                viewLocationButtonHtml = `<button class="btn-mapa" data-order-id="${order.id}" data-location-lat="${order.location.lat}" data-location-lng="${order.location.lng}">Ver Ubicación</button>`;
            }

            orderDiv.innerHTML = `
                <h3>${order.nombre} <span class="status-badge ${statusBadgeClass}">${statusText}</span> <span style="font-size: 0.7em; color: var(--text-color-dark);">(${orderTypeLabel})</span></h3>
                <p><b>Descripción:</b> ${order.descripcion}</p>
                <p><b>Cantidad:</b> ${order.cantidad}</p>
                <p><b>Precio Sugerido:</b> S/ ${order.precio.toFixed(2)}</p>
                ${ropaDetails}
                ${itemImage}
                <p><b>Método de Pago:</b> ${order.metodoPago}</p>
                <p><b>Dirección de Entrega:</b> ${order.direccion}</p>
                ${compradorInfo ? `<p>${compradorInfo}</p>` : ''}
                <div class="negociacion-historial" id="historial-${order.id}">
                    <h4>Historial de Negociación:</h4>
                    ${order.ofertas.length === 0 ? '<p>No hay ofertas aún.</p>' : ''}
                    ${order.ofertas.map(offer => `
                        <div>
                            <strong>${offer.user}:</strong> S/ ${offer.price.toFixed(2)}
                            <span style="font-size: 0.8em; color: #777;">(${new Date(offer.timestamp).toLocaleString()})</span>
                            <span style="font-weight: 600; margin-left: 5px; color: ${offer.status === 'accepted' ? 'var(--status-success)' : offer.status === 'rejected' ? 'var(--status-danger)' : 'var(--status-warning)'};">${offer.status === 'pending' ? '(Pendiente)' : offer.status === 'accepted' ? '(Aceptada)' : '(Rechazada)'}</span>
                        </div>
                    `).join('')}
                </div>
                <div>
                    ${order.estado === 'abierto' ? `<button class="btn-eliminar-pedido" data-order-id="${order.id}">Eliminar Pedido</button>` : ''}
                    ${order.comprador && (order.estado === 'en_negociacion' || order.estado === 'aceptado') ?
                    `<button class="btn-chat" data-order-id="${order.id}">Abrir Chat</button>` : ''}
                    ${order.estado === 'aceptado' && order.comprador && !order.calificado ?
                    `<button class="btn-calificar-comprador" data-order-id="${order.id}" data-target-user="${order.comprador}">Calificar ${order.type === 'request' ? 'Comprador' : 'Interesado'}</button>` : ''}
                    ${order.estado === 'aceptado' && order.comprador && users[currentUser].rank === 'owner' ?
                    `<button class="btn-finalizar-pedido" data-order-id="${order.id}">Finalizar ${order.type === 'request' ? 'Pedido' : 'Venta'}</button>` : ''}
                    ${viewLocationButtonHtml}
                </div>
            `;
            if (listaTusPedidos) listaTusPedidos.appendChild(orderDiv);
        });

        addYourOrderButtonListeners();
    }

    /**
     * Handles offers and counter-offers for an order.
     * @param {string} orderId - The ID of the order.
     * @param {string} type - 'ofertar' or 'review_offer'.
     * @param {number} [offerPrice] - The offer price (optional).
     */
    function handleOffer(orderId, type, offerPrice = null) {
        const order = orders.find(o => o.id === orderId);
        if (!order) return;

        if (type === 'ofertar') {
            if (modalNegociacionTitulo) modalNegociacionTitulo.textContent = `💬 Ofertar por "${order.nombre}"`;
            if (modalTexto) modalTexto.innerHTML = `Precio sugerido: <strong>S/ ${order.precio.toFixed(2)}</strong>.`;
            if (modalInputPrecio) {
                modalInputPrecio.style.display = 'block';
                modalInputPrecio.value = '';
            }
            if (btnAceptarOferta) btnAceptarOferta.style.display = 'none';
            if (btnRechazarOferta) btnRechazarOferta.style.display = 'none';
            if (btnContraofertar) {
                btnContraofertar.textContent = 'Enviar Oferta';
                btnContraofertar.dataset.orderId = orderId;
                btnContraofertar.onclick = () => {
                    const price = parseFloat(modalInputPrecio.value);
                    if (isNaN(price) || price <= 0) {
                        showToast('Ingresa un precio válido.', 'warning', '⚠️');
                        return;
                    }
                    if (order.estado === 'aceptado' || order.estado === 'completado' || order.estado === 'cancelado' || order.estado === 'rechazado' || order.estado === 'vendido') {
                        showToast('Este pedido ya no está disponible para ofertas.', 'danger', '❌');
                        hideModal('modal-negociacion');
                        return;
                    }

                    let finalPrice = price;
                    // Apply student discount if applicable
                    if (users[currentUser]?.rank === 'student') {
                        finalPrice = price * 0.90;
                        showToast(`¡Aplicado 10% de descuento de estudiante! Nueva oferta: S/ ${finalPrice.toFixed(2)}`, 'info', '✨');
                    }

                    const newOffer = {
                        user: currentUser,
                        price: finalPrice,
                        timestamp: Date.now(),
                        status: 'pending'
                    };
                    order.ofertas.push(newOffer);
                    order.comprador = currentUser;
                    order.estado = 'en_negociacion';
                    saveOrders();
                    renderOrders();
                    renderProposedOrders();
                    renderYourOrders();
                    showToast('¡Oferta enviada con éxito!', 'success', '✅');
                    hideModal('modal-negociacion');
                };
            }
            if (btnCancelarNegociacion) btnCancelarNegociacion.onclick = () => hideModal('modal-negociacion');
            renderNegotiationHistory(order);
            showModal('modal-negociacion');
        } else if (type === 'review_offer' && order.solicitante === currentUser) {
            const lastOffer = order.ofertas[order.ofertas.length - 1];
            if (!lastOffer || lastOffer.status !== 'pending') {
                showToast('No hay ofertas pendientes para revisar.', 'info', 'ℹ️');
                return;
            }

            if (modalNegociacionTitulo) modalNegociacionTitulo.textContent = `💬 Oferta de ${lastOffer.user} por "${order.nombre}"`;
            if (modalTexto) modalTexto.innerHTML = `Precio ofrecido: <strong>S/ ${lastOffer.price.toFixed(2)}</strong>.`;
            if (modalInputPrecio) {
                modalInputPrecio.style.display = 'block';
                modalInputPrecio.value = lastOffer.price.toFixed(2);
            }

            if (btnAceptarOferta) {
                btnAceptarOferta.style.display = 'inline-block';
                btnAceptarOferta.onclick = () => {
                    lastOffer.status = 'accepted';
                    order.estado = 'aceptado';
                    order.comprador = lastOffer.user;
                    saveOrders();
                    renderOrders();
                    renderProposedOrders();
                    renderYourOrders();
                    showToast(`¡Oferta de ${lastOffer.user} aceptada!`, 'success', '🎉');
                    hideModal('modal-negociacion');
                };
            }

            if (btnRechazarOferta) {
                btnRechazarOferta.style.display = 'inline-block';
                btnRechazarOferta.onclick = () => {
                    lastOffer.status = 'rejected';
                    const hasOtherPendingOffers = order.ofertas.some(o => o.status === 'pending' && o !== lastOffer);
                    if (!hasOtherPendingOffers) {
                        order.estado = 'abierto';
                        order.comprador = null;
                    }
                    saveOrders();
                    renderOrders();
                    renderProposedOrders();
                    renderYourOrders();
                    showToast(`Oferta de ${lastOffer.user} rechazada.`, 'danger', '❌');
                    hideModal('modal-negociacion');
                };
            }

            if (btnContraofertar) {
                btnContraofertar.textContent = 'Contraofertar';
                btnContraofertar.onclick = () => {
                    const counterPrice = parseFloat(modalInputPrecio.value);
                    if (isNaN(counterPrice) || counterPrice <= 0) {
                        showToast('Ingresa un precio válido para la contraoferta.', 'warning', '⚠️');
                        return;
                    }
                    lastOffer.status = 'rejected';
                    const newOffer = {
                        user: currentUser,
                        price: counterPrice,
                        timestamp: Date.now(),
                        status: 'pending'
                    };
                    order.ofertas.push(newOffer);
                    order.estado = 'en_negociacion';
                    saveOrders();
                    renderOrders();
                    renderProposedOrders();
                    renderYourOrders();
                    showToast('¡Contraoferta enviada!', 'info', '🔄');
                    hideModal('modal-negociacion');
                };
            }
            if (btnCancelarNegociacion) btnCancelarNegociacion.onclick = () => hideModal('modal-negociacion');
            renderNegotiationHistory(order);
            showModal('modal-negociacion');
        }
    }

    /**
     * Renders the negotiation history of an order in the modal.
     * @param {object} order - The order object.
     */
    function renderNegotiationHistory(order) {
        if (historialNegociacion) historialNegociacion.innerHTML = '<h4>Historial de Negociación:</h4>';
        if (order.ofertas.length === 0) {
            if (historialNegociacion) historialNegociacion.innerHTML += '<p>No hay ofertas aún.</p>';
            return;
        }

        order.ofertas.forEach(offer => {
            const offerDiv = document.createElement('div');
            let statusColor = '';
            let statusText = '';
            if (offer.status === 'accepted') {
                statusColor = 'var(--status-success)';
                statusText = 'Aceptada';
            } else if (offer.status === 'rejected') {
                statusColor = 'var(--status-danger)';
                statusText = 'Rechazada';
            } else {
                statusColor = 'var(--status-warning)';
                statusText = 'Pendiente';
            }

            const offerClass = offer.user === order.solicitante ? 'oferta-solicitante' : 'oferta-comprador';

            offerDiv.innerHTML = `
                <div class="${offerClass}">
                    <strong>${offer.user}:</strong> S/ ${offer.price.toFixed(2)}
                    <span style="font-size: 0.8em; color: #777;">(${new Date(offer.timestamp).toLocaleString()})</span>
                    <span style="font-weight: 600; margin-left: 5px; color: ${statusColor};">(${statusText})</span>
                </div>
            `;
            if (historialNegociacion) historialNegociacion.appendChild(offerDiv);
        });
    }

    /**
     * Toggles the visibility of an order (hide/show).
     * @param {string} orderId - The ID of the order.
     */
    function toggleHideOrder(orderId) {
        const orderIndex = orders.findIndex(o => o.id === orderId);
        if (orderIndex > -1) {
            orders[orderIndex].oculto = !orders[orderIndex].oculto;
            saveOrders();
            renderOrders();
            renderProposedOrders();
            showToast(orders[orderIndex].oculto ? 'Pedido ocultado.' : 'Pedido mostrado.', 'info', orders[orderIndex].oculto ? '🙈' : '👀');
        }
    }

    /**
     * Deletes an order. Only the owner or an "open" order can be deleted.
     * @param {string} orderId - The ID of the order.
     */
    function deleteOrder(orderId) {
        const orderIndex = orders.findIndex(o => o.id === orderId && o.solicitante === currentUser);
        if (orderIndex > -1) {
            if (orders[orderIndex].estado !== 'abierto' && users[currentUser].rank !== 'owner') {
                 showToast('Solo se pueden eliminar pedidos en estado "abierto".', 'danger', '❌');
                 return;
            }

            orders.splice(orderIndex, 1);
            saveOrders();
            renderYourOrders();
            showToast('Pedido eliminado exitosamente.', 'success', '🗑️');
        }
    }

    /**
     * Marks an order as finalized (only for the owner).
     * @param {string} orderId - The ID of the order.
     */
    function finalizeOrder(orderId) {
        const order = orders.find(o => o.id === orderId);
        if (order && users[currentUser].rank === 'owner') {
            order.estado = order.type === 'request' ? 'completado' : 'vendido'; // Differentiate status for proposed items
            saveOrders();
            renderYourOrders();
            renderOrders();
            renderProposedOrders();
            showToast('Pedido marcado como finalizado.', 'success', '✅');
        } else if (!order) {
            showToast('Pedido no encontrado.', 'danger', '❌');
        } else {
            showToast('Solo los propietarios pueden finalizar pedidos.', 'danger', '❌');
        }
    }


    // =========================================================================
    // 8. Rating System
    // =========================================================================

    /**
     * Opens the rating modal.
     * @param {string} orderId - ID of the order to rate.
     * @param {string} targetUser - User to be rated.
     * @param {boolean} ratingSolicitante - True if rating the requester, false if rating the buyer.
     */
    function openRatingModal(orderId, targetUser, ratingSolicitante) {
        if (!currentUser) {
            showToast('Debes iniciar sesión para calificar.', 'danger', '❌');
            return;
        }
        currentRatingOrderId = orderId;
        currentRatingTargetUser = targetUser;
        isRatingSolicitante = ratingSolicitante;

        if (calificarUsuarioTarget) calificarUsuarioTarget.textContent = targetUser;
        if (inputCalificacion) inputCalificacion.value = '';
        if (inputComentarioCalificacion) inputComentarioCalificacion.value = '';
        showModal('modal-calificacion');
    }

    /**
     * Sends the rating and comment to the target user.
     */
    function sendRating() {
        const score = parseInt(inputCalificacion.value);
        const comment = inputComentarioCalificacion.value.trim();

        if (isNaN(score) || score < 1 || score > 5) {
            showToast('Por favor, ingresa una puntuación entre 1 y 5.', 'warning', '⚠️');
            return;
        }

        if (!users[currentRatingTargetUser]) {
            showToast('Usuario a calificar no encontrado.', 'danger', '❌');
            return;
        }

        users[currentRatingTargetUser].calificaciones.push({
            rater: currentUser,
            score: score,
            comment: comment,
            timestamp: Date.now()
        });

        const order = orders.find(o => o.id === currentRatingOrderId);
        if (order) {
            order.calificado = true; // Mark the order as rated
        }
        saveUsers();
        saveOrders(); // Save order status

        showToast(`¡Calificación enviada a ${currentRatingTargetUser}!`, 'success', '⭐');
        hideModal('modal-calificacion');
        renderPerfil(); // Update profile to reflect the new rating
        renderOrders();
        renderProposedOrders();
        renderYourOrders();
    }


    // =========================================================================
    // 9. Chat Functionality
    // =========================================================================

    /**
     * Opens the chat modal for a specific order.
     * @param {string} orderId - The ID of the order.
     */
    function openChatModal(orderId) {
        currentChatOrderId = orderId;
        const order = orders.find(o => o.id === orderId);
        if (!order) return;

        if (chatTitulo) chatTitulo.textContent = `💬 Chat del Pedido: "${order.nombre}"`;
        renderChatMessages(order.chat, chatMessages);
        showModal('modal-chat');
        if (chatMessages) chatMessages.scrollTop = chatMessages.scrollHeight; // Scroll to end of chat
    }

    /**
     * Opens the chat modal for a specific friend.
     * @param {string} friendUsername - The friend's username.
     */
    function openFriendChatModal(friendUsername) {
        currentFriendChatUser = friendUsername;

        // Create a consistent chat ID for two users
        const chatUsers = [currentUser, friendUsername].sort();
        const chatId = `friend_${chatUsers[0]}_${chatUsers[1]}`;

        if (!messages[chatId]) {
            messages[chatId] = [];
            saveMessages();
        }

        if (friendChatTitulo) friendChatTitulo.textContent = `💬 Chat con ${friendUsername}`;
        renderChatMessages(messages[chatId], friendChatMessages);
        showModal('modal-friend-chat');
        if (friendChatMessages) friendChatMessages.scrollTop = friendChatMessages.scrollHeight; // Scroll to end of chat
    }

    /**
     * Renders chat messages in a given container.
     * @param {Array<object>} chatArray - Array of message objects.
     * @param {HTMLElement} chatContainer - The HTML container where messages will be displayed.
     */
    function renderChatMessages(chatArray, chatContainer) {
        if (chatContainer) chatContainer.innerHTML = '';
        chatArray.forEach(msg => {
            const msgDiv = document.createElement('div');
            msgDiv.classList.add('chat-message');
            msgDiv.classList.add(msg.sender === currentUser ? 'self' : 'other');
            msgDiv.innerHTML = `
                <strong>${msg.sender}:</strong>
                <p>${msg.message}</p>
                <small>${new Date(msg.timestamp).toLocaleTimeString()}</small>
            `;
            if (chatContainer) chatContainer.appendChild(msgDiv);
        });
    }

    /**
     * Sends a message in the order chat.
     */
    function sendChatMessage() {
        const message = chatMessageInput.value.trim();
        if (!message || !currentChatOrderId) return;

        const order = orders.find(o => o.id === currentChatOrderId);
        if (!order) return;

        order.chat.push({
            sender: currentUser,
            message: message,
            timestamp: Date.now()
        });
        saveOrders();
        renderChatMessages(order.chat, chatMessages);
        if (chatMessageInput) chatMessageInput.value = '';
        if (chatMessages) chatMessages.scrollTop = chatMessages.scrollHeight;
    }

    /**
     * Sends a message in the friend chat.
     */
    function sendFriendChatMessage() {
        const message = friendChatMessageInput.value.trim();
        if (!message || !currentFriendChatUser) return;

        const chatUsers = [currentUser, currentFriendChatUser].sort();
        const chatId = `friend_${chatUsers[0]}_${chatUsers[1]}`;

        if (!messages[chatId]) {
            messages[chatId] = [];
        }

        messages[chatId].push({
            sender: currentUser,
            message: message,
            timestamp: Date.now()
        });
        saveMessages();
        renderChatMessages(messages[chatId], friendChatMessages);
        if (friendChatMessageInput) friendChatMessageInput.value = '';
        if (friendChatMessages) friendChatMessages.scrollTop = friendChatMessages.scrollHeight;
    }


    // =========================================================================
    // 10. Friend Management
    // =========================================================================

    /**
     * Renders the current user's friend list.
     */
    function renderFriends() {
        if (listaAmigos) listaAmigos.innerHTML = '';
        const userFriends = friends[currentUser] || [];

        if (userFriends.length === 0) {
            if (listaAmigos) listaAmigos.innerHTML = '<p>Aún no tienes amigos. ¡Busca y añade algunos!</p>';
            return;
        }

        userFriends.forEach(friend => {
            const friendDiv = document.createElement('div');
            friendDiv.classList.add('friend-item');
            friendDiv.innerHTML = `
                <span>${friend}</span>
                <div>
                    <button class="btn-chat" data-friend-user="${friend}">Chat</button>
                    <button class="btn-reject" data-friend-remove="${friend}">Eliminar</button>
                </div>
            `;
            if (listaAmigos) listaAmigos.appendChild(friendDiv);
        });
        addFriendButtonListeners();
    }

    /**
     * Renders friend requests received by the current user.
     */
    function renderFriendRequests() {
        if (solicitudesAmistadRecibidas) solicitudesAmistadRecibidas.innerHTML = '';
        const requestsForCurrentUser = friendRequests[currentUser] || [];

        if (requestsForCurrentUser.length === 0) {
            if (solicitudesAmistadRecibidas) solicitudesAmistadRecibidas.innerHTML = '<p>No tienes solicitudes de amistad pendientes.</p>';
            return;
        }

        requestsForCurrentUser.forEach(requester => {
            const requestDiv = document.createElement('div');
            requestDiv.classList.add('friend-request');
            requestDiv.innerHTML = `
                <span>${requester} te ha enviado una solicitud de amistad.</span>
                <div>
                    <button class="btn-accept" data-requester="${requester}">Aceptar</button>
                    <button class="btn-reject" data-requester="${requester}">Rechazar</button>
                </div>
            `;
            if (solicitudesAmistadRecibidas) solicitudesAmistadRecibidas.appendChild(requestDiv);
        });
        addFriendRequestListeners();
    }

    /**
     * Sends a friend request to another user.
     * @param {string} targetUser - The username to send the request to.
     */
    function sendFriendRequest(targetUser) {
        if (!targetUser || targetUser === currentUser) {
            showToast('No puedes enviarte una solicitud a ti mismo.', 'warning', '⚠️');
            return;
        }
        if (!users[targetUser]) {
            showToast('Usuario no encontrado.', 'danger', '❌');
            return;
        }
        if ((friends[currentUser] && friends[currentUser].includes(targetUser)) || (friends[targetUser] && friends[targetUser].includes(currentUser))) {
            showToast(`${targetUser} ya es tu amigo.`, 'info', 'ℹ️');
            return;
        }
        if (friendRequests[targetUser] && friendRequests[targetUser].includes(currentUser)) {
            showToast(`Ya enviaste una solicitud a ${targetUser}.`, 'info', 'ℹ️');
            return;
        }
        if (friendRequests[currentUser] && friendRequests[currentUser].includes(targetUser)) {
            showToast(`${targetUser} ya te envió una solicitud. ¡Acéptala!`, 'info', 'ℹ️');
            return;
        }

        if (!friendRequests[targetUser]) {
            friendRequests[targetUser] = [];
        }
        friendRequests[targetUser].push(currentUser);
        saveFriendRequests();
        showToast(`Solicitud de amistad enviada a ${targetUser}.`, 'success', '✉️');
    }

    /**
     * Accepts a friend request.
     * @param {string} requester - The username who sent the request.
     */
    function acceptFriendRequest(requester) {
        if (!friendRequests[currentUser]) return;

        friendRequests[currentUser] = friendRequests[currentUser].filter(r => r !== requester);

        if (!friends[currentUser]) friends[currentUser] = [];
        if (!friends[requester]) friends[requester] = [];
        friends[currentUser].push(requester);
        friends[requester].push(currentUser);

        saveFriendRequests();
        saveFriends();
        showToast(`Ahora eres amigo de ${requester}.`, 'success', '🤝');
        renderFriendRequests();
        renderFriends();
    }

    /**
     * Rejects a friend request.
     * @param {string} requester - The username who sent the request.
     */
    function rejectFriendRequest(requester) {
        if (!friendRequests[currentUser]) return;

        friendRequests[currentUser] = friendRequests[currentUser].filter(r => r !== requester);
        saveFriendRequests();
        showToast(`Solicitud de ${requester} rechazada.`, 'info', '👋');
        renderFriendRequests();
    }

    /**
     * Removes a friend from the list.
     * @param {string} friendToRemove - The username of the friend to remove.
     */
    function removeFriend(friendToRemove) {
        if (friends[currentUser]) {
            friends[currentUser] = friends[currentUser].filter(f => f !== friendToRemove);
        }
        if (friends[friendToRemove]) {
            friends[friendToRemove] = friends[friendToRemove].filter(f => f !== currentUser);
        }
        saveFriends();
        showToast(`${friendToRemove} ha sido eliminado de tus amigos.`, 'info', '💔');
        renderFriends();
    }


    // =========================================================================
    // 11. Location Management (Geolocation and Google Maps)
    // =========================================================================

    /**
     * Attempts to get the user's current geolocation.
     * Also handles permission requests.
     * IMPORTANT: Geolocation API only works in secure contexts (HTTPS).
     * @param {Function} callback - A callback function that receives the location ({lat, lng}) or null in case of error.
     */
    function getLocation(callback) {
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(
                (position) => {
                    const { latitude, longitude } = position.coords;
                    callback({ lat: latitude, lng: longitude }, null);
                },
                (error) => {
                    let errorMessage = 'No se pudo obtener tu ubicación. Por favor, revisa los permisos del navegador.';
                    if (error.code === error.PERMISSION_DENIED) {
                        errorMessage = "Acceso a la ubicación denegado. Por favor, habilita los permisos de ubicación para esta página en la configuración de tu navegador.";
                    }
                    showToast(errorMessage, 'danger', '❌');
                    callback(null, errorMessage);
                }
            );
        } else {
            showToast('Tu navegador no soporta geolocalización.', 'danger', '❌');
            callback(null, 'Browser does not support geolocation.');
        }
    }

    /**
     * Updates the user's location in their profile.
     */
    function updateMyGeolocation() {
        showToast('Obteniendo tu ubicación...', 'info', '⏳');
        getLocation((location, error) => {
            if (location) {
                if (users[currentUser]) {
                    users[currentUser].location = location;
                    saveUsers();
                    showToast('Ubicación actualizada con éxito.', 'success', '📍');
                    renderPerfil();
                }
            } else {
                showToast('No se pudo actualizar tu ubicación.', 'danger', '❌');
            }
        });
    }

    /**
     * Dynamically loads the Google Maps API script.
     * @param {Function} callback - Function to execute once the API is loaded.
     */
    function loadGoogleMapsScript(callback) {
        if (window.google && window.google.maps) {
            callback(); // If already loaded, execute callback directly
            return;
        }
        const script = document.createElement('script');
        script.src = `https://maps.googleapis.com/maps/api/js?key=${GOOGLE_MAPS_API_KEY}&callback=initMap`;
        script.async = true;
        script.defer = true;
        document.head.appendChild(script);
        window.initMap = callback; // Set the global callback for Google Maps API
    }

    /**
     * Displays the current user's location on a Google Map.
     * Also shows coordinates in a toast.
     */
    function showMyLocationOnMap() {
        showToast('Obteniendo tu ubicación...', 'info', '⏳');
        getLocation((location, error) => {
            if (location) {
                showToast(`Tu ubicación actual: Lat: ${location.lat.toFixed(4)}, Lng: ${location.lng.toFixed(4)}`, 'info', '🗺️');
                // Optionally, save to user profile if not already saved
                if (users[currentUser] && !users[currentUser].location) {
                    users[currentUser].location = location;
                    saveUsers();
                }
                loadGoogleMapsScript(() => {
                    initMapWithLocation(location);
                    showModal('modal-google-map');
                });
            } else {
                showToast('No se pudo obtener tu ubicación para mostrar en el mapa.', 'danger', '❌');
            }
        });
    }

    /**
     * Displays a specific location (from an order) on a Google Map.
     * @param {object} location - Location object {lat, lng}.
     */
    function showOrderLocationOnMap(location) {
        if (!location || typeof location.lat === 'undefined' || typeof location.lng === 'undefined') {
            showToast('Ubicación del pedido no disponible o inválida.', 'danger', '❌');
            return;
        }
        showToast(`Ubicación del pedido: Lat: ${location.lat.toFixed(4)}, Lng: ${location.lng.toFixed(4)}`, 'info', '🗺️');
        loadGoogleMapsScript(() => {
            initMapWithLocation(location);
            showModal('modal-google-map');
        });
    }

    /**
     * Initializes the Google Maps map with a specific location.
     * @param {object} location - Location object {lat, lng}.
     */
    function initMapWithLocation(location) {
        if (!map) {
            map = new google.maps.Map(mapDiv, {
                center: location,
                zoom: 15,
                mapId: 'DEMO_MAP_ID', // You can create a custom map ID in Google Cloud Console
                disableDefaultUI: true, // Hide default UI controls
                zoomControl: true, // Show zoom controls
                streetViewControl: false, // Hide Street View control
                fullscreenControl: false, // Hide fullscreen control
                mapTypeControl: false, // Hide map type control
                scaleControl: false, // Hide scale control
                rotateControl: false, // Hide rotation control
            });
        } else {
            map.setCenter(location);
        }

        if (mapMarker) {
            mapMarker.setMap(null); // Remove old marker if exists
        }
        mapMarker = new google.maps.Marker({
            position: location,
            map: map,
            title: 'Ubicación',
            animation: google.maps.Animation.DROP,
        });

        // Optionally, add an info window
        const infoWindow = new google.maps.InfoWindow({
            content: `<b>Ubicación</b><br>Lat: ${location.lat.toFixed(4)}, Lng: ${location.lng.toFixed(4)}`
        });
        mapMarker.addListener('click', () => {
            infoWindow.open(map, mapMarker);
        });
        infoWindow.open(map, mapMarker); // Open info window by default
    }


    // =========================================================================
    // 12. Reporting System
    // =========================================================================

    /**
     * Opens the modal to report a user.
     * @param {string} username - The username to report.
     */
    function openReportModal(username) {
        if (!currentUser) {
            showToast('Debes iniciar sesión para reportar un usuario.', 'danger', '❌');
            return;
        }
        if (username === currentUser) {
            showToast('No puedes reportarte a ti mismo.', 'warning', '⚠️');
            return;
        }
        currentUserToReport = username;
        if (reportarUsernameTarget) reportarUsernameTarget.textContent = username;
        if (inputRazonReporte) inputRazonReporte.value = '';
        showModal('modal-reportar');
    }

    /**
     * Sends a user report.
     */
    function sendReport() {
        const reason = inputRazonReporte.value.trim();
        if (!reason) {
            showToast('Por favor, ingresa una razón para el reporte.', 'warning', '⚠️');
            return;
        }

        const newReport = {
            id: Date.now().toString(),
            reporter: currentUser,
            reportedUser: currentUserToReport,
            reason: reason,
            timestamp: Date.now(),
            status: 'pending'
        };
        reports.push(newReport);
        saveReports();
        showToast(`Reporte enviado contra ${currentUserToReport}. Gracias por tu ayuda.`, 'success', '🚨');
        hideModal('modal-reportar');
    }


    // =========================================================================
    // 13. Donation Function
    // =========================================================================

    /**
     * Confirms a donation and updates the user's rank if applicable.
     */
    function confirmDonation() {
        const amount = parseFloat(inputMontoDonacion.value);
        if (isNaN(amount) || amount <= 0) {
            showToast('Por favor, ingresa un monto válido.', 'warning', '⚠️');
            return;
        }

        showToast(`¡Gracias por tu donación de S/ ${amount.toFixed(2)}!`, 'success', '💖');

        // If the user is not owner or creator, they become a donor
        if (users[currentUser] && users[currentUser].rank !== 'owner' && users[currentUser].rank !== 'creator') {
            users[currentUser].rank = 'donor';
            saveUsers();
            renderPerfil(); // Update profile to reflect the new rank
        }
        hideModal('modal-donar');
        if (inputMontoDonacion) inputMontoDonacion.value = '';
    }


    // =========================================================================
    // 14. Rank Management (Student Code)
    // =========================================================================

    /**
     * Opens the modal to enter the student code.
     */
    function getStudentCode() {
        showModal('modal-student-code');
    }

    /**
     * Submits the student code for validation and rank update.
     */
    function submitStudentCode() {
        const code = inputStudentCode.value.trim();
        if (!code) {
            showToast('Por favor, ingresa tu código de estudiante.', 'warning', '⚠️');
            return;
        }

        // Student code validation simulation
        if (code.startsWith('STUDENT-') && code.length > 10) {
            if (users[currentUser] && users[currentUser].rank === 'new') {
                users[currentUser].rank = 'student';
                saveUsers();
                showToast('¡Código de estudiante validado! Ahora eres un estudiante.', 'success', '🎓');
                renderPerfil();
                hideModal('modal-student-code');
            } else {
                 showToast('Tu rango actual no permite cambiar a estudiante de esta forma.', 'warning', '⚠️');
                 hideModal('modal-student-code');
            }
        } else {
            showToast('Código de estudiante inválido. Intenta de nuevo.', 'danger', '❌');
        }
    }


    // =========================================================================
    // 15. User Profile Management
    // =========================================================================

    /**
     * Renders the current user's profile information.
     */
    function renderPerfil() {
        if (!currentUser) {
            showLoginRegisterZone();
            return;
        }

        // Ensure the user's profile exists or create it by default
        const user = users[currentUser];
        if (!user) {
            users[currentUser] = { ...createDefaultUserProfile(currentUser), ...users[currentUser] };
            saveUsers();
        }

        if (perfilUsernameDisplay) perfilUsernameDisplay.textContent = currentUser;
        if (perfilRankBadge) {
            perfilRankBadge.textContent = user.rank;
            perfilRankBadge.className = `rank-badge ${user.rank}`; // Apply the rank CSS class
        }
        if (ratingValueDisplay) ratingValueDisplay.textContent = calculateUserRating(currentUser);
        if (perfilDescripcion) perfilDescripcion.value = user.description || '';
        if (inputLema) inputLema.value = user.lema || '';
        if (perfilLema) perfilLema.textContent = user.lema || 'Sin lema';

        if (perfilFoto) perfilFoto.src = user.profilePicture || 'https://via.placeholder.com/120/007bff/ffffff?text=Perfil';

        if (ocultarDireccionCheckbox) ocultarDireccionCheckbox.checked = user.hideAddress || false;

        // Show location and update button
        if (user.location) {
            if (perfilUbicacion) perfilUbicacion.innerHTML = `<b>Mi ubicación:</b> Lat: ${user.location.lat.toFixed(4)}, Lng: ${user.location.lng.toFixed(4)} <button id="btn-actualizar-ubicacion">Actualizar mi ubicación</button>`;
            const btnActualizarUbicacionInPerfil = document.getElementById('btn-actualizar-ubicacion');
            if (btnActualizarUbicacionInPerfil) {
                btnActualizarUbicacionInPerfil.onclick = updateMyGeolocation;
            }
        } else {
            if (perfilUbicacion) perfilUbicacion.innerHTML = `<b>Mi ubicación:</b> No disponible <button id="btn-actualizar-ubicacion">Actualizar mi ubicación</button>`;
            const btnActualizarUbicacionInPerfil = document.getElementById('btn-actualizar-ubicacion');
            if (btnActualizarUbicacionInPerfil) {
                btnActualizarUbicacionInPerfil.onclick = updateMyGeolocation;
            }
        }

        // Show benefits based on rank
        if (studentBenefitsDiv) studentBenefitsDiv.style.display = user.rank === 'student' ? 'block' : 'none';
        if (donorBenefitsDiv) donorBenefitsDiv.style.display = user.rank === 'donor' ? 'block' : 'none';
        if (creatorBenefitsDiv) creatorBenefitsDiv.style.display = user.rank === 'creator' ? 'block' : 'none';
        if (btnObtenerCodigoEstudiante) btnObtenerCodigoEstudiante.style.display = (user.rank === 'new') ? 'inline-block' : 'none';

        renderYourOrders(); // Render orders created by the user
        renderFriends(); // Render friend list
        renderFriendRequests(); // Render friend requests
    }

    /**
     * Saves changes made to the user's profile.
     */
    function saveProfileChanges() {
        if (!currentUser) return;

        if (perfilDescripcion) users[currentUser].description = perfilDescripcion.value.trim();
        if (inputLema) users[currentUser].lema = inputLema.value.trim();
        if (ocultarDireccionCheckbox) users[currentUser].hideAddress = ocultarDireccionCheckbox.checked;
        saveUsers();
        showToast('Perfil actualizado con éxito.', 'success', '💾');
        renderPerfil();
    }

    /**
     * Triggers the upload of a new profile photo.
     */
    function handleProfileImageUpload() {
        if (inputPerfilFoto) inputPerfilFoto.click();
    }


    // =========================================================================
    // 16. Owner Profile Display
    // =========================================================================

    /**
     * Displays the modal with the owner's profile information.
     */
    function showOwnerProfileModal() {
        const ownerUser = users[OWNER_USERNAME];
        if (!ownerUser) {
            showToast('El perfil del propietario no está disponible.', 'danger', '❌');
            return;
        }

        if (ownerProfilePhoto) ownerProfilePhoto.src = ownerUser.profilePicture || 'https://placehold.co/120x120/dc3545/ffffff?text=Owner';
        if (ownerProfileUsernameDisplay) ownerProfileUsernameDisplay.textContent = ownerUser.username || OWNER_USERNAME;
        if (ownerProfileLema) ownerProfileLema.textContent = ownerUser.lema || 'El creador de ChambAPP.';
        if (ownerProfileDescription) ownerProfileDescription.textContent = ownerUser.description || 'Este es el perfil del administrador principal de ChambAPP. Mi objetivo es conectar a la comunidad y facilitar el intercambio de bienes y servicios.';
        if (ownerRankBadge) {
            ownerRankBadge.textContent = ownerUser.rank;
            ownerRankBadge.className = `rank-badge ${ownerUser.rank}`;
        }
        if (ownerProfileRatingValue) ownerProfileRatingValue.textContent = calculateUserRating(OWNER_USERNAME);

        showModal('modal-owner-profile');
    }


    // =========================================================================
    // 17. Event Management (Listeners)
    // =========================================================================

    /**
     * Adds event listeners to available order buttons.
     * Called every time orders are rendered.
     */
    function addOrderButtonListeners() {
        document.querySelectorAll('.btn-ofertar').forEach(button => {
            button.onclick = (event) => {
                handleOffer(event.target.dataset.orderId, 'ofertar');
            };
        });

        document.querySelectorAll('.btn-chat').forEach(button => {
            button.onclick = (event) => {
                openChatModal(event.target.dataset.orderId);
            };
        });

        document.querySelectorAll('.btn-calificar-solicitante').forEach(button => {
            button.onclick = (event) => {
                openRatingModal(event.target.dataset.orderId, event.target.dataset.targetUser, true);
            };
        });

        document.querySelectorAll('.btn-reportar').forEach(button => {
            button.onclick = (event) => {
                openReportModal(event.target.dataset.targetUser);
            };
        });

        document.querySelectorAll('.btn-ocultar-pedido').forEach(button => {
            button.onclick = (event) => {
                toggleHideOrder(event.target.dataset.orderId);
            };
        });

        document.querySelectorAll('.btn-add-friend').forEach(button => {
            button.onclick = (event) => {
                sendFriendRequest(event.target.dataset.targetUser);
            };
        });

        document.querySelectorAll('.btn-accept-friend-prompt').forEach(button => {
            button.onclick = (event) => {
                acceptFriendRequest(event.target.dataset.requester);
            };
        });

        document.querySelectorAll('.btn-mapa').forEach(button => {
            button.onclick = (event) => {
                const lat = parseFloat(event.target.dataset.locationLat);
                const lng = parseFloat(event.target.dataset.locationLng);
                if (!isNaN(lat) && !isNaN(lng)) {
                    showOrderLocationOnMap({ lat, lng });
                } else {
                    showToast('Coordenadas de ubicación no válidas para este pedido.', 'danger', '❌');
                }
            };
        });
    }

    /**
     * Adds event listeners to buttons of orders created by the user.
     * Called every time own orders are rendered.
     */
    function addYourOrderButtonListeners() {
        document.querySelectorAll('.btn-eliminar-pedido').forEach(button => {
            button.onclick = (event) => {
                deleteOrder(event.target.dataset.orderId);
            };
        });

        document.querySelectorAll('.negociacion-historial').forEach(historyDiv => {
            const orderId = historyDiv.id.replace('historial-', '');
            const order = orders.find(o => o.id === orderId);
            if (order && order.solicitante === currentUser && order.estado === 'en_negociacion') {
                const lastOffer = order.ofertas[order.ofertas.length - 1];
                if (lastOffer && lastOffer.status === 'pending' && lastOffer.user !== currentUser) {
                    const reviewButton = document.createElement('button');
                    reviewButton.textContent = 'Revisar Oferta Pendiente';
                    reviewButton.classList.add('btn-counter');
                    reviewButton.style.marginTop = '10px';
                    reviewButton.onclick = () => { handleOffer(orderId, 'review_offer'); };
                    historyDiv.parentNode.insertBefore(reviewButton, historyDiv.nextSibling);
                }
            }
        });

        document.querySelectorAll('.btn-chat').forEach(button => {
            button.onclick = (event) => {
                openChatModal(event.target.dataset.orderId);
            };
        });

        document.querySelectorAll('.btn-calificar-comprador').forEach(button => {
            button.onclick = (event) => {
                openRatingModal(event.target.dataset.orderId, event.target.dataset.targetUser, false);
            };
        });

        document.querySelectorAll('.btn-finalizar-pedido').forEach(button => {
            button.onclick = (event) => {
                finalizeOrder(event.target.dataset.orderId);
            };
        });

        document.querySelectorAll('.btn-mapa').forEach(button => {
            button.onclick = (event) => {
                const lat = parseFloat(event.target.dataset.locationLat);
                const lng = parseFloat(event.target.dataset.locationLng);
                if (!isNaN(lat) && !isNaN(lng)) {
                    showOrderLocationOnMap({ lat, lng });
                } else {
                    showToast('Coordenadas de ubicación no válidas para este pedido.', 'danger', '❌');
                }
            };
        });
    }


    /**
     * Adds event listeners to friend request buttons.
     * Called every time requests are rendered.
     */
    function addFriendRequestListeners() {
        document.querySelectorAll('#solicitudesAmistadRecibidas .btn-accept').forEach(button => {
            button.onclick = (event) => {
                acceptFriendRequest(event.target.dataset.requester);
            };
        });
        document.querySelectorAll('#solicitudesAmistadRecibidas .btn-reject').forEach(button => {
            button.onclick = (event) => {
                rejectFriendRequest(event.target.dataset.requester);
            };
        });
    }

    /**
     * Adds event listeners to friend list buttons.
     * Called every time friends are rendered.
     */
    function addFriendButtonListeners() {
        document.querySelectorAll('#listaAmigos .btn-chat').forEach(button => {
            button.onclick = (event) => {
                openFriendChatModal(event.target.dataset.friendUser);
            };
        });
        document.querySelectorAll('#listaAmigos .btn-reject').forEach(button => {
            button.onclick = (event) => {
                removeFriend(event.target.dataset.friendRemove);
            };
        });
    }

    /**
     * Initializes all main application event listeners.
     */
    function initAppListeners() {
        console.log('[ChambAPP Debug] initAppListeners called.');
        // Login/Register Zone
        if (btnRegistrar) btnRegistrar.addEventListener('click', register);
        if (btnLogin) btnLogin.addEventListener('click', login);
        const viewTermsLink = document.getElementById('view-terms');
        if (viewTermsLink) {
            viewTermsLink.addEventListener('click', (e) => {
                e.preventDefault();
                showToast('Términos y condiciones: Al usar ChambAPP, aceptas el uso de tus datos para el funcionamiento de la aplicación, incluyendo tu ubicación para servicios de pedidos y la interacción con otros usuarios. Tus datos no serán compartidos con terceros sin tu consentimiento explícito.', 'info', '📄');
            });
        }

        // Main Menu Zone
        if (btnMisPedidosYArticulos) btnMisPedidosYArticulos.addEventListener('click', navigateToMisPedidosYArticulos); // NEW
        if (btnExplorarPedidos) btnExplorarPedidos.addEventListener('click', navigateToRequestsCatalog);
        if (btnExplorarPropuestas) btnExplorarPropuestas.addEventListener('click', navigateToProposedCatalog);
        if (btnVerPerfil) btnVerPerfil.addEventListener('click', navigateToProfile);
        if (btnUtilidades) btnUtilidades.addEventListener('click', navigateToUtilidades); // NEW
        if (btnCerrarSesion) btnCerrarSesion.addEventListener('click', () => { showModal('modal-logout-confirm'); });
        if (btnConfirmLogout) btnConfirmLogout.addEventListener('click', logout);

        // Mis Pedidos y Artículos Zone (NEW)
        if (btnCrearPedido) btnCrearPedido.addEventListener('click', navigateToCreateRequestOrderCategorySelection);
        if (btnProponerArticulo) btnProponerArticulo.addEventListener('click', navigateToProposeArticle);
        if (btnVerMisPedidos) btnVerMisPedidos.addEventListener('click', () => {
            navigateToProfile(); // Go to profile
            const yourOrdersSection = document.getElementById('listaTusPedidos');
            if (yourOrdersSection) {
                yourOrdersSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
                showToast('Navegando a tus pedidos...', 'info', '🛒');
            }
        });
        if (btnVerMisPropuestas) btnVerMisPropuestas.addEventListener('click', () => {
            navigateToProfile(); // Go to profile
            const yourOrdersSection = document.getElementById('listaTusPedidos'); // Reuse the same section for both types
            if (yourOrdersSection) {
                yourOrdersSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
                showToast('Navegando a tus artículos propuestos...', 'info', '🛍️');
            }
        });
        if (btnVolverMisPedidosYArticulos) btnVolverMisPedidosYArticulos.addEventListener('click', navigateToMainMenu);

        // Utilidades Zone (NEW)
        if (btnShowOnGoogleMaps) btnShowOnGoogleMaps.addEventListener('click', showMyLocationOnMap);
        if (btnDonarUtilidades) btnDonarUtilidades.addEventListener('click', () => { showModal('modal-donar'); });
        if (btnViewOwnerProfile) btnViewOwnerProfile.addEventListener('click', showOwnerProfileModal);
        if (btnVolverUtilidades) btnVolverUtilidades.addEventListener('click', navigateToMainMenu);


        // Category Selection Zone
        btnSeleccionarCategoria.forEach(button => {
            button.addEventListener('click', (event) => {
                const categoria = event.target.dataset.categoria;
                showToast(`Creando pedido de ${categoria}...`, 'info', '📦');
                // inputOrderType is already set to 'request' by navigateToCreateRequestOrderCategorySelection
                showScreen(crearEditarPedidoScreen);
            });
        });
        if (btnVolverSeleccionCategoria) btnVolverSeleccionCategoria.addEventListener('click', navigateToMisPedidosYArticulos);

        // Create/Edit Order Zone
        if (isRopaCheckbox) isRopaCheckbox.addEventListener('change', () => {
            if (ropaFields) ropaFields.style.display = isRopaCheckbox.checked ? 'block' : 'none';
        });
        if (btnAutocompletarDireccion) btnAutocompletarDireccion.addEventListener('click', () => {
            getLocation((location) => {
                if (location) {
                    if (inputDireccion) inputDireccion.value = `Lat: ${location.lat.toFixed(4)}, Lng: ${location.lng.toFixed(4)}`;
                    showToast('Ubicación GPS obtenida. Puedes añadir detalles adicionales de la dirección manualmente.', 'info', '📍');
                }
            });
        });
        if (btnCrearPedidoSolicitante) btnCrearPedidoSolicitante.addEventListener('click', createOrder);
        if (btnVolverCrearEditar) btnVolverCrearEditar.addEventListener('click', navigateToMisPedidosYArticulos); // Changed back button target

        if (btnUploadImage) btnUploadImage.addEventListener('click', () => {
            if (inputImagenArticulo) inputImagenArticulo.click();
        });
        if (inputImagenArticulo) inputImagenArticulo.addEventListener('change', (event) => {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (e) => {
                    currentArticleImageBase64 = e.target.result;
                    if (previewImagenArticulo) previewImagenArticulo.innerHTML = `<img src="${e.target.result}" alt="">`;
                    showToast('Imagen seleccionada.', 'info', '🖼️');
                };
                reader.readAsDataURL(file);
            } else {
                if (previewImagenArticulo) previewImagenArticulo.innerHTML = '<p style="color: var(--text-color-dark); font-style: italic;">Sin imagen seleccionada</p>';
                currentArticleImageBase64 = null;
            }
        });

        // Requests Catalog Zone (Comprador Screen)
        if (btnVolverComprador) btnVolverComprador.addEventListener('click', navigateToMainMenu);
        if (toggleOcultosBtn) toggleOcultosBtn.addEventListener('click', () => {
            showingHiddenOrders = !showingHiddenOrders;
            toggleOcultosBtn.textContent = showingHiddenOrders ? '↩️ Ocultar Pedidos Ocultos' : '🔄 Mostrar Pedidos Ocultos';
            renderOrders();
        });

        // Proposed Catalog Zone
        if (btnVolverPropuestas) btnVolverPropuestas.addEventListener('click', navigateToMainMenu);
        if (toggleOcultosBtnPropuestas) toggleOcultosBtnPropuestas.addEventListener('click', () => {
            showingHiddenProposedOrders = !showingHiddenProposedOrders;
            toggleOcultosBtnPropuestas.textContent = showingHiddenProposedOrders ? '↩️ Ocultar Artículos Ocultos' : '🔄 Mostrar Artículos Ocultos';
            renderProposedOrders();
        });

        // Profile Zone
        if (perfilFotoContainer) perfilFotoContainer.addEventListener('click', handleProfileImageUpload);
        if (inputPerfilFoto) inputPerfilFoto.addEventListener('change', (event) => {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (e) => {
                    if (perfilFoto) perfilFoto.src = e.target.result;
                    users[currentUser].profilePicture = e.target.result;
                    saveUsers();
                    showToast('Foto de perfil actualizada.', 'success', '📸');
                };
                reader.readAsDataURL(file);
            }
        });
        if (btnGuardarPerfil) btnGuardarPerfil.addEventListener('click', saveProfileChanges);
        if (btnVolverPerfil) btnVolverPerfil.addEventListener('click', navigateToMainMenu);
        if (btnConfirmarDonacion) btnConfirmarDonacion.addEventListener('click', confirmDonation);
        if (btnCancelarDonacion) btnCancelarDonacion.addEventListener('click', () => { hideModal('modal-donar'); });
        if (btnObtenerCodigoEstudiante) btnObtenerCodigoEstudiante.addEventListener('click', getStudentCode);
        if (btnSubmitStudentCode) btnSubmitStudentCode.addEventListener('click', submitStudentCode);
        if (btnCancelStudentCode) btnCancelStudentCode.addEventListener('click', () => { hideModal('modal-student-code'); });
        if (btnShowFriends) btnShowFriends.addEventListener('click', () => {
            const friendsSection = document.getElementById('listaAmigos');
            if (friendsSection) {
                friendsSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
                showToast('Navegando a tus amigos...', 'info', '👥');
            }
        });

        // Modal Listeners
        if (btnEnviarCalificacion) btnEnviarCalificacion.addEventListener('click', sendRating);
        if (btnCancelarCalificacion) btnCancelarCalificacion.addEventListener('click', () => { hideModal('modal-calificacion'); });
        if (btnEnviarMensaje) btnEnviarMensaje.addEventListener('click', sendChatMessage);
        if (chatMessageInput) chatMessageInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') { sendChatMessage(); }
        });
        if (btnCerrarChat) btnCerrarChat.addEventListener('click', () => { hideModal('modal-chat'); });
        if (btnEnviarFriendMessage) btnEnviarFriendMessage.addEventListener('click', sendFriendChatMessage);
        if (friendChatMessageInput) friendChatMessageInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') { sendFriendChatMessage(); }
        });
        if (btnCerrarFriendChat) btnCerrarFriendChat.addEventListener('click', () => { hideModal('modal-friend-chat'); });
        if (btnEnviarReporte) btnEnviarReporte.addEventListener('click', sendReport);
        if (btnCancelarReporte) btnCancelarReporte.addEventListener('click', () => { hideModal('modal-reportar'); });
    }

    // =========================================================================
    // 18. Initial Application Setup
    // =========================================================================

    // This ensures the DOM is fully loaded before trying to access elements
    document.addEventListener('DOMContentLoaded', () => {
        console.log('[ChambAPP Debug] DOMContentLoaded event fired.');
        initAppListeners(); // Initialize all event listeners

        // Check if a user is already logged in from a previous session
        if (currentUser) {
            console.log('[ChambAPP Debug] User found in session storage:', currentUser);
            updateUIForCurrentUser(); // Update UI for the logged-in user
            navigateToMainMenu(); // Go to main menu
        } else {
            console.log('[ChambAPP Debug] No user found in session storage. Showing login/register.');
            showLoginRegisterZone(); // Show login/register screen
        }

        // Initialize OWNER profile if it doesn't exist
        if (!users[OWNER_USERNAME]) {
            console.log('[ChambAPP Debug] Initializing OWNER profile.');
            const ownerProfile = createDefaultUserProfile(OWNER_USERNAME);
            ownerProfile.password = OWNER_PASSWORD;
            ownerProfile.rank = 'owner';
            ownerProfile.lema = 'El Fundador de ChambAPP';
            ownerProfile.description = 'Este es el perfil del administrador principal de ChambAPP. Mi objetivo es conectar a la comunidad y facilitar el intercambio de bienes y servicios.';
            ownerProfile.profilePicture = 'https://placehold.co/120x120/800080/ffffff?text=OWNER'; // A distinct image for the owner
            users[OWNER_USERNAME] = ownerProfile;
            saveUsers();
        }
    });

</script>
</body>
</html>
