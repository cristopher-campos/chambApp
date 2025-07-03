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


button {
    margin: 12px 10px;
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
.btn-counter:hover { background-color: #f7d900; box-shadow: 0 4px 12px rgba(0,0,0,0.3), 0 0 15px var(--status-warning); transform: translateY(-1px) scale(1.02);}
.btn-calificar { background-color: var(--accent-color); box-shadow: 0 2px 8px rgba(0,0,0,0.2), 0 0 5px var(--accent-color); }
.btn-calificar:hover { background-color: #c737e0; box-shadow: 0 4px 12px rgba(0,0,0,0.3), 0 0 15px var(--accent-color); transform: translateY(-1px) scale(1.02);}


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

.pedido .btn-mapa,
.pedido .btn-chat,
.friend-item .btn-chat {
    background-color: var(--status-info); /* Electric blue */
    margin-top: 15px;
    padding: 10px 20px;
    font-size: 0.9em;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(41, 121, 255, 0.3), 0 0 8px var(--status-info); /* Blue glow */
    transition: all 0.2s ease;
    display: inline-block;
    min-width: unset;
    color: var(--background-dark); /* Darker text */
    text-transform: uppercase;
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
    justify-content: flex-end;
    gap: 12px;
    margin-top: 25px;
}
.modal-buttons button {
    padding: 12px 25px;
    font-size: 0.9em;
    border-radius: 8px;
    margin: 0;
    color: var(--background-dark); /* Ensure text is dark */
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
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
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
}
.btn-add-friend:hover, .btn-accept-friend-prompt:hover {
    background-color: var(--secondary-dark);
    box-shadow: 0 4px 12px rgba(41, 121, 255, 0.4);
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

/* Floating Donate Button */
#btn-floating-donar {
    position: fixed;
    bottom: 25px;
    right: 25px;
    z-index: 1001;
    padding: 16px 25px;
    font-size: 1.1em;
    border-radius: 50px;
    background: linear-gradient(45deg, var(--accent-color) 0%, #2979ff 100%); /* Purple to Blue gradient */
    color: white;
    box-shadow: 0 5px 20px rgba(0,0,0,0.4), 0 0 15px var(--accent-color); /* Stronger shadow with glow */
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
        margin: 8px 6px;
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
    #btn-floating-donar {
        bottom: 20px;
        padding: 14px 22px;
        font-size: 1.0em;
    }
    #btn-floating-donar {
        right: 20px;
    }

    .creditos, .version-info {
        font-size: 0.7em;
        bottom: 10px;
    }
    .creditos { right: 15px; }
    .version-info { left: 15px; }
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
    #btn-floating-donar {
        bottom: 15px;
        padding: 12px 18px;
        font-size: 0.9em;
    }
    #btn-floating-donar {
        right: 15px;
    }
    .creditos, .version-info {
        font-size: 0.65em;
        bottom: 5px;
    }
}
</style>
</head>
<body>

<h1><span style="font-size: 0.8em;">🚀</span> ChambAPP</h1>
<div id="toast"><span id="toast-icon"></span><span id="toast-message"></span></div>

<div id="login-register" class="visible pantalla">
<h2>🔐 Acceso al Sistema</h2>
<input type="text" id="reg-usuario" placeholder="Nombre de usuario" autocomplete="username" />
<input type="password" id="reg-password" placeholder="Contraseña (mín. 6 caracteres, mayús, minús, número)" autocomplete="current-password" />
<div style="text-align: left; margin-top: 15px; margin-bottom: 10px;">
    <input type="checkbox" id="consent-checkbox" />
    <label for="consent-checkbox" style="font-size: 0.9em; color: var(--text-color-dark);">Acepto los <a href="#" id="view-terms" style="color: var(--secondary-color); text-decoration: underline;">términos y condiciones</a> y entiendo el uso de mi ubicación para los servicios de la app.</label>
</div>
<button id="btn-registrar">📝 Registrarse</button>
<button id="btn-login">🔑 Iniciar Sesión</button>
</div>

<div id="menu-principal" class="pantalla">
<div class="saludo" id="saludoUsuario"></div>
<button id="btn-crear-pedido">📦 Crear Pedido</button>
<button id="btn-ver-pedidos">🛒 Ver Pedidos</button><br />
<button id="btn-show-my-location">📍 Mostrar mi ubicación GPS</button><br />
<button id="btn-ver-perfil">👤 Ver Perfil</button><br />
<button id="btn-view-owner-profile">👑 Ver Perfil del Propietario</button><br /><br />
<button id="btn-cerrar-sesion">🚪 Cerrar Sesion</button>
</div>

<!-- NUEVA PANTALLA: SELECCIÓN DE CATEGORÍA -->
<div id="seleccionar-categoria" class="pantalla">
    <h2>Elegir Categoría de Pedido</h2>
    <div style="display: flex; flex-direction: column; gap: 15px; width: 100%;">
        <button class="btn-seleccionar-categoria" data-categoria="Ropa">👕 Ropa</button>
        <button class="btn-seleccionar-categoria" data-categoria="Comida Rápida">🍔 Comida Rápida</button>
        <button class="btn-seleccionar-categoria" data-categoria="Electrónica">💻 Electrónica</button>
        <button class="btn-seleccionar-categoria" data-categoria="Servicios">🔧 Servicios</button>
        <button class="btn-seleccionar-categoria" data-categoria="Otros">📦 Otros</button>
    </div>
    <br /><br />
    <button id="btn-volver-seleccion-categoria">⬅️ Volver al Panel</button>
</div>

<div id="solicitante" class="pantalla">
<h2>📦 Crear un pedido</h2>
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
    <input id="inputDireccion" placeholder="Dirección de entrega (ej. Calle Falsa 123, Ventanilla)" />
    <button id="btn-autocompletar-direccion">📍 Usar mi ubicación actual</button>
</div>

<button id="btn-crear-pedido-solicitante">Crear Pedido</button><br /><br />
<button id="btn-volver-solicitante">⬅️ Volver</button>
</div>

<div id="comprador" class="pantalla">
<h2>🛒 Pedidos disponibles</h2>
<button id="toggleOcultosBtn" class="btn-ocultar-pedido">🔄 Mostrar Pedidos Ocultos</button>
<div id="listaPedidos"></div>
<button id="btn-volver-comprador">⬅️ Volver</button>
</div>

<div id="perfil" class="pantalla">
<h2>👤 Perfil de usuario</h2>
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

<button id="btn-guardar-perfil">💾 Guardar Cambios del Perfil</button>

<div id="studentBenefits" style="display:none;">
<p style="font-style: italic; color: var(--rank-student-color);">✨ Como estudiante, disfrutas de un 10% de descuento en tus ofertas.</p>
<button id="btn-obtener-codigo-estudiante">🎓 Obtener Código Estudiante</button>
</div>
<div id="donorBenefits" style="display:none;">
<p style="font-style: italic; color: var(--rank-donor-color);">💖 ¡Gracias por tu generosidad! Tu apoyo hace que ChambAPP sea posible.</p>
</div>
<div id="creatorBenefits" style="display:none;">
<p style="font-style: italic; color: var(--rank-creator-color);">🌟 ¡Eres un creador increíble en nuestra comunidad!</p>
</div>

<h3>Tus Pedidos Creados:</h3>
<div id="listaTusPedidos"></div>

<h3>Tus Amigos:</h3>
<div id="listaAmigos"></div>
<button id="btn-show-friends">👥 Ver Amigos</button>

<h3>Solicitudes de Amistad Recibidas:</h3>
<div id="solicitudesAmistadRecibidas"></div>
</div>
<button id="btn-volver-perfil">⬅️ Volver</button>
</div>

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

<!-- New modal for owner profile -->
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

<!-- New modal for logout confirmation -->
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

<button id="btn-floating-donar" style="display:none;">💖 Donar</button> <!-- Floating Donate Button (initially hidden) -->

<div class="creditos">© 2024 ChambAPP. Desarrollado por tus amigos de la universidad.</div>
<div class="version-info">Version 0.04 Alpha</div>

<script>
// Dummy Data
let users = JSON.parse(localStorage.getItem('users')) || {};
let currentUser = JSON.parse(sessionStorage.getItem('currentUser'));
let orders = JSON.parse(localStorage.getItem('orders')) || [];
let friendRequests = JSON.parse(localStorage.getItem('friendRequests')) || {}; // {targetUser: [requester1, requester2]}
let friends = JSON.parse(localStorage.getItem('friends')) || {}; // {user1: [friend1, friend2]}
let messages = JSON.parse(localStorage.getItem('messages')) || {}; // {chatId: [{sender, message, timestamp}]}
let reports = JSON.parse(localStorage.getItem('reports')) || [];

// Initialize default profile data for new users
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
    };
}


// DOM Elements
const loginRegisterScreen = document.getElementById('login-register');
const menuPrincipalScreen = document.getElementById('menu-principal');
const seleccionarCategoriaScreen = document.getElementById('seleccionar-categoria');
const solicitanteScreen = document.getElementById('solicitante');
const compradorScreen = document.getElementById('comprador');
const perfilScreen = document.getElementById('perfil');

const regUsuarioInput = document.getElementById('reg-usuario');
const regPasswordInput = document.getElementById('reg-password');
const consentCheckbox = document.getElementById('consent-checkbox');
const btnRegistrar = document.getElementById('btn-registrar');
const btnLogin = document.getElementById('btn-login');

const saludoUsuario = document.getElementById('saludoUsuario');
const btnCrearPedido = document.getElementById('btn-crear-pedido');
const btnVerPedidos = document.getElementById('btn-ver-pedidos');
const btnShowMyLocation = document.getElementById('btn-show-my-location'); // Changed from btnVerMapaGPS
const btnVerPerfil = document.getElementById('btn-ver-perfil');
const btnCerrarSesion = document.getElementById('btn-cerrar-sesion');
const btnViewOwnerProfile = document.getElementById('btn-view-owner-profile');


// Category Selection buttons
const btnSeleccionarCategoria = document.querySelectorAll('.btn-seleccionar-categoria');
const btnVolverSeleccionCategoria = document.getElementById('btn-volver-seleccion-categoria');


const inputNombre = document.getElementById('inputNombre');
const inputDescripcion = document.getElementById('inputDescripcion');
const inputCantidad = document.getElementById('inputCantidad');
const inputPrecio = document.getElementById('inputPrecio');
const inputMetodoPago = document.getElementById('inputMetodoPago');
const inputDireccion = document.getElementById('inputDireccion');
const btnCrearPedidoSolicitante = document.getElementById('btn-crear-pedido-solicitante');
const btnVolverSolicitante = document.getElementById('btn-volver-solicitante');
const isRopaCheckbox = document.getElementById('isRopaCheckbox');
const ropaFields = document.getElementById('ropaFields');
const inputTalla = document.getElementById('inputTalla');
const inputGenero = document.getElementById('inputGenero');
const btnAutocompletarDireccion = document.getElementById('btn-autocompletar-direccion');
const inputImagenArticulo = document.getElementById('inputImagenArticulo');
const btnUploadImage = document.getElementById('btn-upload-image');
const previewImagenArticulo = document.getElementById('previewImagenArticulo');


const listaPedidos = document.getElementById('listaPedidos');
const btnVolverComprador = document.getElementById('btn-volver-comprador');
const toggleOcultosBtn = document.getElementById('toggleOcultosBtn');

// Perfil elements
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

// Removed modalMapa and related elements

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

const btnFloatingDonar = document.getElementById('btn-floating-donar');

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


// Global variable for article image
let currentArticleImageBase64 = null;

// --- Utility Functions (Enhanced) ---

/**
 * Shows a specific screen and hides others.
 * @param {HTMLElement} screenToShow - The screen element to make visible.
 */
function showScreen(screenToShow) {
    const screens = [loginRegisterScreen, menuPrincipalScreen, seleccionarCategoriaScreen, solicitanteScreen, compradorScreen, perfilScreen];
    screens.forEach(screen => {
        screen.classList.remove('visible');
    });
    screenToShow.classList.add('visible');
}

/**
 * Displays a toast notification.
 * @param {string} message - The message to display.
 * @param {string} type - 'success', 'danger', 'warning', or 'info'.
 * @param {string} icon - Emoji or icon character.
 */
function showToast(message, type = 'info', icon = '') {
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
 * Shows a modal overlay.
 * @param {string} modalId - The ID of the modal overlay to show.
 */
function showModal(modalId) {
    const modalOverlay = document.getElementById(modalId);
    if (modalOverlay) {
        modalOverlay.classList.add('visible');
    }
}

/**
 * Hides a modal overlay.
 * @param {string} modalId - The ID of the modal overlay to hide.
 */
function hideModal(modalId) {
    const modalOverlay = document.getElementById(modalId);
    if (modalOverlay) {
        modalOverlay.classList.remove('visible');
    }
}

// --- Data Persistence ---
function saveUsers() {
    localStorage.setItem('users', JSON.stringify(users));
}

function saveOrders() {
    localStorage.setItem('orders', JSON.stringify(orders));
}

function saveFriendRequests() {
    localStorage.setItem('friendRequests', JSON.stringify(friendRequests));
}

function saveFriends() {
    localStorage.setItem('friends', JSON.stringify(friends));
}

function saveMessages() {
    localStorage.setItem('messages', JSON.stringify(messages));
}

function saveReports() {
    localStorage.setItem('reports', JSON.stringify(reports));
}

function setCurrentUser(user) {
    currentUser = user;
    sessionStorage.setItem('currentUser', JSON.stringify(currentUser));
    updateUIForCurrentUser();
}

// --- User Management & Authentication ---
function register() {
    const username = regUsuarioInput.value.trim();
    const password = regPasswordInput.value;

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

    const newUserProfile = createDefaultUserProfile(username);
    newUserProfile.password = password;
    users[username] = newUserProfile;

    saveUsers();
    showToast('Registro exitoso. ¡Ahora puedes iniciar sesión!', 'success', '✅');

    setCurrentUser(username);
    showScreen(menuPrincipalScreen);

    regUsuarioInput.value = '';
    regPasswordInput.value = '';
    consentCheckbox.checked = false;
}

function login() {
    const username = regUsuarioInput.value.trim();
    const password = regPasswordInput.value;

    if (!username || !password) {
        showToast('Por favor, ingresa usuario y contraseña.', 'warning', '⚠️');
        return;
    }

    if (users[username] && users[username].password === password) {
        setCurrentUser(username);
        showToast(`¡Hola de nuevo, ${username}!`, 'success', '👋');
        showScreen(menuPrincipalScreen);
        regUsuarioInput.value = '';
        regPasswordInput.value = '';
    } else {
        showToast('Usuario o contraseña incorrectos.', 'danger', '❌');
    }
}

function logout() {
    setCurrentUser(null);
    showToast('Sesión cerrada. ¡Vuelve pronto!', 'info', '👋');
    hideModal('modal-logout-confirm');
    showScreen(loginRegisterScreen);
}

function updateUIForCurrentUser() {
    if (currentUser) {
        saludoUsuario.textContent = `¡Hola, ${currentUser}!`;
        btnFloatingDonar.style.display = 'flex';
    } else {
        saludoUsuario.textContent = '';
        btnFloatingDonar.style.display = 'none';
    }
}

// --- Order Management ---
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

    if (!nombre || !descripcion || !cantidad || isNaN(precio) || precio <= 0 || !metodoPago || !direccion) {
        showToast('Por favor, completa todos los campos obligatorios del pedido.', 'warning', '⚠️');
        return;
    }

    if (isRopa && (!talla || !genero)) {
        showToast('Por favor, selecciona la talla y género para el artículo de ropa.', 'warning', '⚠️');
        return;
    }

    const newOrder = {
        id: Date.now().toString(),
        solicitante: currentUser,
        nombre,
        descripcion,
        cantidad,
        precio,
        metodoPago,
        direccion,
        isRopa,
        talla,
        genero,
        imageUrl: imageUrl,
        comprador: null,
        estado: 'abierto',
        oculto: false,
        ofertas: [],
        chat: [],
        calificado: false
    };

    orders.push(newOrder);
    saveOrders();
    showToast('¡Pedido creado con éxito!', 'success', '✅');
    showScreen(menuPrincipalScreen);
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

let showingHiddenOrders = false;

function renderOrders() {
    if (listaPedidos) listaPedidos.innerHTML = '';

    let ordersToDisplay = orders.filter(order => order.solicitante !== currentUser);

    if (!showingHiddenOrders) {
        ordersToDisplay = ordersToDisplay.filter(order => !order.oculto);
    }

    if (ordersToDisplay.length === 0) {
        if (listaPedidos) listaPedidos.innerHTML = '<p>No hay pedidos disponibles en este momento.</p>';
        return;
    }

    ordersToDisplay.forEach(order => {
        const orderDiv = document.createElement('div');
        orderDiv.classList.add('pedido');
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
            </div>
        `;
        if (listaPedidos) listaPedidos.appendChild(orderDiv);
    });

    addOrderButtonListeners();
}

function renderYourOrders() {
    if (listaTusPedidos) listaTusPedidos.innerHTML = '';
    const yourOrders = orders.filter(order => order.solicitante === currentUser);

    if (yourOrders.length === 0) {
        if (listaTusPedidos) listaTusPedidos.innerHTML = '<p>No has creado ningún pedido aún.</p>';
        return;
    }

    yourOrders.forEach(order => {
        const orderDiv = document.createElement('div');
        orderDiv.classList.add('pedido');
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

        let compradorInfo = order.comprador ? `<b>Comprador:</b> ${order.comprador}` : '';

        let ropaDetails = '';
        if (order.isRopa) {
            ropaDetails = `<p><b>Talla:</b> ${order.talla} | <b>Género:</b> ${order.genero}</p>`;
        }
        const itemImage = order.imageUrl ? `<img src="${order.imageUrl}" alt="" class="pedido-imagen">` : '';

        orderDiv.innerHTML = `
            <h3>${order.nombre} <span class="status-badge ${statusBadgeClass}">${statusText}</span></h3>
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
                `<button class="btn-calificar-comprador" data-order-id="${order.id}" data-target-user="${order.comprador}">Calificar Comprador</button>` : ''}
                ${order.estado === 'aceptado' && order.comprador && users[currentUser].rank === 'owner' ?
                `<button class="btn-finalizar-pedido" data-order-id="${order.id}">Finalizar Pedido</button>` : ''}
            </div>
        `;
        if (listaTusPedidos) listaTusPedidos.appendChild(orderDiv);
    });

    addYourOrderButtonListeners();
}

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
                if (order.estado === 'aceptado' || order.estado === 'completado' || order.estado === 'cancelado' || order.estado === 'rechazado') {
                    showToast('Este pedido ya no está disponible para ofertas.', 'danger', '❌');
                    hideModal('modal-negociacion');
                    return;
                }

                let finalPrice = price;
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


function toggleHideOrder(orderId) {
    const orderIndex = orders.findIndex(o => o.id === orderId);
    if (orderIndex > -1) {
        orders[orderIndex].oculto = !orders[orderIndex].oculto;
        saveOrders();
        renderOrders();
        showToast(orders[orderIndex].oculto ? 'Pedido ocultado.' : 'Pedido mostrado.', 'info', orders[orderIndex].oculto ? '🙈' : '👀');
    }
}

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

function finalizeOrder(orderId) {
    const order = orders.find(o => o.id === orderId);
    if (order && users[currentUser].rank === 'owner') {
        order.estado = 'completado';
        saveOrders();
        renderYourOrders();
        renderOrders();
        showToast('Pedido marcado como finalizado.', 'success', '✅');
    } else if (!order) {
        showToast('Pedido no encontrado.', 'danger', '❌');
    } else {
        showToast('Solo los propietarios pueden finalizar pedidos.', 'danger', '❌');
    }
}


// --- Rating System ---
let currentRatingOrderId = null;
let currentRatingTargetUser = null;
let isRatingSolicitante = false;

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
        order.calificado = true;
    }
    saveUsers();
    saveOrders();

    showToast(`¡Calificación enviada a ${currentRatingTargetUser}!`, 'success', '⭐');
    hideModal('modal-calificacion');
    renderPerfil();
    renderOrders();
    renderYourOrders();
}

function calculateUserRating(username) {
    if (!users[username] || users[username].calificaciones.length === 0) {
        return 'No calificado aún';
    }
    const totalScore = users[username].calificaciones.reduce((sum, c) => sum + c.score, 0);
    const averageScore = (totalScore / users[username].calificaciones.length).toFixed(1);
    return `${averageScore} (${users[username].calificaciones.length} calificaciones)`;
}

// --- Chat Functionality ---
let currentChatOrderId = null;
let currentFriendChatUser = null;

function openChatModal(orderId) {
    currentChatOrderId = orderId;
    const order = orders.find(o => o.id === orderId);
    if (!order) return;

    if (chatTitulo) chatTitulo.textContent = `💬 Chat del Pedido: "${order.nombre}"`;
    renderChatMessages(order.chat, chatMessages);
    showModal('modal-chat');
    if (chatMessages) chatMessages.scrollTop = chatMessages.scrollHeight;
}

function openFriendChatModal(friendUsername) {
    currentFriendChatUser = friendUsername;

    const chatUsers = [currentUser, friendUsername].sort();
    const chatId = `friend_${chatUsers[0]}_${chatUsers[1]}`;

    if (!messages[chatId]) {
        messages[chatId] = [];
        saveMessages();
    }

    if (friendChatTitulo) friendChatTitulo.textContent = `💬 Chat con ${friendUsername}`;
    renderChatMessages(messages[chatId], friendChatMessages);
    showModal('modal-friend-chat');
    if (friendChatMessages) friendChatMessages.scrollTop = friendChatMessages.scrollHeight;
}

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

// --- Friend Management ---
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

function rejectFriendRequest(requester) {
    if (!friendRequests[currentUser]) return;

    friendRequests[currentUser] = friendRequests[currentUser].filter(r => r !== requester);
    saveFriendRequests();
    showToast(`Solicitud de ${requester} rechazada.`, 'info', '👋');
    renderFriendRequests();
}

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

// --- Location (Simple Geolocator) ---

/**
 * Attempts to get the current geolocation of the user.
 * It also handles permission requests.
 * IMPORTANT: Geolocation API only works on secure contexts (HTTPS).
 * @param {Function} callback - A callback function that receives the location ({lat, lng}) or null on error.
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

function showMyLocation() {
    showToast('Obteniendo tu ubicación...', 'info', '⏳');
    getLocation((location, error) => {
        if (location) {
            showToast(`Tu ubicación actual: Lat: ${location.lat.toFixed(4)}, Lng: ${location.lng.toFixed(4)}`, 'info', '🗺️');
            // Optionally, save to user profile if not already saved via updateMyGeolocation
            if (users[currentUser] && !users[currentUser].location) {
                users[currentUser].location = location;
                saveUsers();
            }
        } else {
            showToast('No se pudo obtener tu ubicación.', 'danger', '❌');
        }
    });
}

// --- Reporting ---
let currentUserToReport = null;

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


// --- Donation Feature ---
function confirmDonation() {
    const amount = parseFloat(inputMontoDonacion.value);
    if (isNaN(amount) || amount <= 0) {
        showToast('Por favor, ingresa un monto válido.', 'warning', '⚠️');
        return;
    }

    showToast(`¡Gracias por tu donación de S/ ${amount.toFixed(2)}!`, 'success', '💖');

    if (users[currentUser] && users[currentUser].rank !== 'owner' && users[currentUser].rank !== 'creator') {
        users[currentUser].rank = 'donor';
        saveUsers();
        renderPerfil();
    }
    hideModal('modal-donar');
    if (inputMontoDonacion) inputMontoDonacion.value = '';
}


// --- Student Code / Rank Management ---
function getStudentCode() {
    showModal('modal-student-code');
}

function submitStudentCode() {
    const code = inputStudentCode.value.trim();
    if (!code) {
        showToast('Por favor, ingresa tu código de estudiante.', 'warning', '⚠️');
        return;
    }

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

// --- Profile Management ---
function renderPerfil() {
    if (!currentUser) {
        showScreen(loginRegisterScreen);
        return;
    }

    const user = users[currentUser];
    if (!user) {
        users[currentUser] = { ...createDefaultUserProfile(currentUser), ...users[currentUser] };
        saveUsers();
    }

    if (perfilUsernameDisplay) perfilUsernameDisplay.textContent = currentUser;
    if (perfilRankBadge) {
        perfilRankBadge.textContent = user.rank;
        perfilRankBadge.className = `rank-badge ${user.rank}`;
    }
    if (ratingValueDisplay) ratingValueDisplay.textContent = calculateUserRating(currentUser);
    if (perfilDescripcion) perfilDescripcion.value = user.description || '';
    if (inputLema) inputLema.value = user.lema || '';
    if (perfilLema) perfilLema.textContent = user.lema || 'Sin lema';

    if (perfilFoto) perfilFoto.src = user.profilePicture || 'https://via.placeholder.com/120/007bff/ffffff?text=Perfil';

    if (ocultarDireccionCheckbox) ocultarDireccionCheckbox.checked = user.hideAddress || false;

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

    if (studentBenefitsDiv) studentBenefitsDiv.style.display = user.rank === 'student' ? 'block' : 'none';
    if (donorBenefitsDiv) donorBenefitsDiv.style.display = user.rank === 'donor' ? 'block' : 'none';
    if (creatorBenefitsDiv) creatorBenefitsDiv.style.display = user.rank === 'creator' ? 'block' : 'none';
    if (btnObtenerCodigoEstudiante) btnObtenerCodigoEstudiante.style.display = (user.rank === 'new') ? 'inline-block' : 'none';

    renderYourOrders();
    renderFriends();
    renderFriendRequests();
}

function saveProfileChanges() {
    if (!currentUser) return;

    if (perfilDescripcion) users[currentUser].description = perfilDescripcion.value.trim();
    if (inputLema) users[currentUser].lema = inputLema.value.trim();
    if (ocultarDireccionCheckbox) users[currentUser].hideAddress = ocultarDireccionCheckbox.checked;
    saveUsers();
    showToast('Perfil actualizado con éxito.', 'success', '💾');
    renderPerfil();
}


// --- Image Upload (Profile & Article) ---
function handleProfileImageUpload() {
    if (inputPerfilFoto) inputPerfilFoto.click();
}


// --- Owner Profile Display ---
function showOwnerProfileModal() {
    const ownerUser = users['owner'];
    if (!ownerUser) {
        showToast('El perfil del propietario no está disponible.', 'danger', '❌');
        return;
    }

    if (ownerProfilePhoto) ownerProfilePhoto.src = ownerUser.profilePicture || 'https://placehold.co/120x120/dc3545/ffffff?text=Owner';
    if (ownerProfileUsernameDisplay) ownerProfileUsernameDisplay.textContent = ownerUser.username || 'Propietario';
    if (ownerProfileLema) ownerProfileLema.textContent = ownerUser.lema || 'El creador de ChambAPP.';
    if (ownerProfileDescription) ownerProfileDescription.textContent = ownerUser.description || 'Este es el perfil del administrador principal de ChambAPP.';
    if (ownerRankBadge) {
        ownerRankBadge.textContent = ownerUser.rank;
        ownerRankBadge.className = `rank-badge ${ownerUser.rank}`;
    }
    if (ownerProfileRatingValue) ownerProfileRatingValue.textContent = calculateUserRating('owner');

    showModal('modal-owner-profile');
}


// --- Event Listeners ---

// Initial setup
document.addEventListener('DOMContentLoaded', () => {

    for (const username in users) {
        users[username] = { ...createDefaultUserProfile(username), ...users[username] };
    }
    if (!users['owner']) {
        users['owner'] = createDefaultUserProfile('owner');
        users['owner'].password = 'ADMIN123';
        users['owner'].rank = 'owner';
        users['owner'].lema = 'Impulsando ChambAPP para todos.';
        users['owner'].description = 'Soy el fundador de ChambAPP, dedicado a construir una comunidad de ayuda mutua.';
        users['owner'].profilePicture = 'https://placehold.co/120x120/dc3545/ffffff?text=Owner';
    } else {
        users['owner'].password = 'ADMIN123';
        users['owner'].rank = 'owner';
        users['owner'].lema = users['owner'].lema || 'Impulsando ChambAPP para todos.';
        users['owner'].description = users['owner'].description || 'Este es el perfil del administrador principal de ChambAPP.';
        users['owner'].profilePicture = users['owner'].profilePicture || 'https://placehold.co/120x120/dc3545/ffffff?text=Owner';
    }
    saveUsers();

    updateUIForCurrentUser();
    if (currentUser) {
        showScreen(menuPrincipalScreen);
    } else {
        showScreen(loginRegisterScreen);
    }

    const viewTermsLink = document.getElementById('view-terms');
    if (viewTermsLink) {
        viewTermsLink.addEventListener('click', (e) => {
            e.preventDefault();
            showToast('Términos y condiciones: Al usar ChambAPP, aceptas el uso de tus datos para el funcionamiento de la aplicación, incluyendo tu ubicación para servicios de pedidos y la interacción con otros usuarios. Tus datos no serán compartidos con terceros sin tu consentimiento explícito.', 'info', '📄');
        });
    }

    // Login/Register Screen
    if (btnRegistrar) btnRegistrar.addEventListener('click', register);
    if (btnLogin) btnLogin.addEventListener('click', login);

    // Main Menu Screen
    if (btnCrearPedido) btnCrearPedido.addEventListener('click', () => { showScreen(seleccionarCategoriaScreen); });
    if (btnVerPedidos) btnVerPedidos.addEventListener('click', () => {
        showScreen(compradorScreen);
        renderOrders();
    });
    // Changed: from btnVerMapaGPS to btnShowMyLocation
    if (btnShowMyLocation) btnShowMyLocation.addEventListener('click', () => {
        showMyLocation();
    });
    if (btnVerPerfil) btnVerPerfil.addEventListener('click', () => {
        showScreen(perfilScreen);
        renderPerfil();
    });

    if (btnViewOwnerProfile) btnViewOwnerProfile.addEventListener('click', () => { showOwnerProfileModal(); });
    if (btnCerrarSesion) btnCerrarSesion.addEventListener('click', () => { showModal('modal-logout-confirm'); });
    if (btnConfirmLogout) btnConfirmLogout.addEventListener('click', logout);

    // Category Selection Screen
    btnSeleccionarCategoria.forEach(button => {
        button.addEventListener('click', (event) => {
            const categoria = event.target.dataset.categoria;
            showToast(`Creando pedido de ${categoria}...`, 'info', '📦');
            showScreen(solicitanteScreen);
        });
    });
    if (btnVolverSeleccionCategoria) btnVolverSeleccionCategoria.addEventListener('click', () => { showScreen(menuPrincipalScreen); });

    // Solicitante Screen
    if (isRopaCheckbox) isRopaCheckbox.addEventListener('change', () => {
        if (ropaFields) ropaFields.style.display = isRopaCheckbox.checked ? 'block' : 'none';
    });
    if (btnAutocompletarDireccion) btnAutocompletarDireccion.addEventListener('click', () => {
        getLocation((location) => {
            if (location) {
                // Modified to only display lat/lng
                if (inputDireccion) inputDireccion.value = `Lat: ${location.lat.toFixed(4)}, Lng: ${location.lng.toFixed(4)}`;
                showToast('Ubicación GPS obtenida. Puedes añadir detalles adicionales de la dirección manualmente.', 'info', '📍');
            }
        });
    });
    if (btnCrearPedidoSolicitante) btnCrearPedidoSolicitante.addEventListener('click', () => { createOrder(); });
    if (btnVolverSolicitante) btnVolverSolicitante.addEventListener('click', () => { showScreen(menuPrincipalScreen); });

    // Comprador Screen
    if (btnVolverComprador) btnVolverComprador.addEventListener('click', () => { showScreen(menuPrincipalScreen); });
    if (toggleOcultosBtn) toggleOcultosBtn.addEventListener('click', () => {
        showingHiddenOrders = !showingHiddenOrders;
        toggleOcultosBtn.textContent = showingHiddenOrders ? '↩️ Ocultar Pedidos Ocultos' : '🔄 Mostrar Pedidos Ocultos';
        renderOrders();
    });

    // Perfil Screen
    if (perfilFotoContainer) perfilFotoContainer.addEventListener('click', () => { handleProfileImageUpload(); });
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
    if (btnGuardarPerfil) btnGuardarPerfil.addEventListener('click', () => { saveProfileChanges(); });
    if (btnVolverPerfil) btnVolverPerfil.addEventListener('click', () => { showScreen(menuPrincipalScreen); });

    if (btnConfirmarDonacion) btnConfirmarDonacion.addEventListener('click', () => { confirmDonation(); });
    if (btnCancelarDonacion) btnCancelarDonacion.addEventListener('click', () => { hideModal('modal-donar'); });

    if (btnObtenerCodigoEstudiante) btnObtenerCodigoEstudiante.addEventListener('click', () => { getStudentCode(); });
    if (btnSubmitStudentCode) btnSubmitStudentCode.addEventListener('click', () => { submitStudentCode(); });
    if (btnCancelStudentCode) btnCancelStudentCode.addEventListener('click', () => { hideModal('modal-student-code'); });

    if (btnShowFriends) btnShowFriends.addEventListener('click', () => {
        const friendsSection = document.getElementById('listaAmigos');
        if (friendsSection) {
            friendsSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
            showToast('Navegando a tus amigos...', 'info', '👥');
        }
    });

    // Floating Donate Button Listener
    if (btnFloatingDonar) btnFloatingDonar.addEventListener('click', () => { showModal('modal-donar'); });


    // Modal Listeners
    if (btnEnviarCalificacion) btnEnviarCalificacion.addEventListener('click', () => { sendRating(); });
    if (btnCancelarCalificacion) btnCancelarCalificacion.addEventListener('click', () => { hideModal('modal-calificacion'); });

    if (btnEnviarMensaje) btnEnviarMensaje.addEventListener('click', () => { sendChatMessage(); });
    if (chatMessageInput) chatMessageInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            sendChatMessage();
        }
    });
    if (btnCerrarChat) btnCerrarChat.addEventListener('click', () => { hideModal('modal-chat'); });

    if (btnEnviarFriendMessage) btnEnviarFriendMessage.addEventListener('click', () => { sendFriendChatMessage(); });
    if (friendChatMessageInput) friendChatMessageInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            sendFriendChatMessage();
        }
    });
    if (btnCerrarFriendChat) btnCerrarFriendChat.addEventListener('click', () => { hideModal('modal-friend-chat'); });

    if (btnEnviarReporte) btnEnviarReporte.addEventListener('click', () => { sendReport(); });
    if (btnCancelarReporte) btnCancelarReporte.addEventListener('click', () => { hideModal('modal-reportar'); });

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
});

// Dynamic button listeners (attached when content is rendered)
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

    // Removed .btn-mapa functionality for orders

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
}

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

    // Removed .btn-mapa functionality for your orders
}


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

function addFriendButtonListeners() {
    document.querySelectorAll('#listaAmigos .btn-chat').forEach(button => {
        button.onclick = (event) => {
            openFriendChatModal(event.target.dataset.friendUser);
        };
    });
    // Removed .btn-mapa functionality for friends
    document.querySelectorAll('#listaAmigos .btn-reject').forEach(button => {
        button.onclick = (event) => {
            removeFriend(event.target.dataset.friendRemove);
        };
    });
}
</script>
</body>
</html>
