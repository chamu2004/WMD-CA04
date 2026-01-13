<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Coffee Haven - Premium Coffee Experience</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <style>
        /* Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #4A2C2A;
            --secondary: #D4B896;
            --accent: #8B4513;
            --light: #F5F5F5;
            --dark: #2C1810;
            --text: #333333;
            --bg: #F5F5F5;
            --card-bg: #FFFFFF;
            --header-bg: #4A2C2A;
            --footer-bg: #4A2C2A;
            --shadow: rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        .dark-mode {
            --primary: #D4B896;
            --secondary: #4A2C2A;
            --accent: #C19A6B;
            --light: #1A1A1A;
            --dark: #E5E5E5;
            --text: #E5E5E5;
            --bg: #1A1A1A;
            --card-bg: #2D2D2D;
            --header-bg: #1A1A1A;
            --footer-bg: #1A1A1A;
            --shadow: rgba(0, 0, 0, 0.3);
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            line-height: 1.6;
            transition: var(--transition);
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header Styles */
        header {
            background-color: var(--header-bg);
            color: white;
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px var(--shadow);
            transition: var(--transition);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }

        .logo i {
            color: var(--secondary);
            margin-right: 10px;
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 1.5rem;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
            padding: 0.5rem 0;
            position: relative;
            cursor: pointer;
        }

        nav ul li a:hover {
            color: var(--secondary);
        }

        nav ul li a.active {
            color: var(--secondary);
        }

        nav ul li a.active::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--secondary);
        }

        .header-controls {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .theme-toggle {
            background: none;
            border: none;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            transition: var(--transition);
        }

        .theme-toggle:hover {
            color: var(--secondary);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Page Styles */
        .page {
            padding: 2rem 0;
            min-height: calc(100vh - 200px);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(74, 44, 42, 0.8), rgba(74, 44, 42, 0.8)), url('https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            text-align: center;
            padding: 5rem 0;
            border-radius: 10px;
            margin-bottom: 2rem;
            position: relative;
            overflow: hidden;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 2rem;
        }

        .btn {
            display: inline-block;
            background-color: var(--secondary);
            color: var(--primary);
            padding: 0.8rem 1.5rem;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            transition: var(--transition);
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            background-color: #e8d0b3;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px var(--shadow);
        }

        /* Floating Coffee Beans Animation */
        .floating-beans {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: 1;
        }

        .bean {
            position: absolute;
            width: 30px;
            height: 15px;
            background-color: var(--secondary);
            border-radius: 50%;
            opacity: 0.7;
            animation: float 15s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
            }
        }

        /* Section Styles */
        .section-title {
            text-align: center;
            margin-bottom: 2rem;
            color: var(--primary);
            position: relative;
            padding-bottom: 10px;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background-color: var(--secondary);
        }

        /* Features Section */
        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .feature-card {
            background-color: var(--card-bg);
            padding: 2rem;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 5px 15px var(--shadow);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: var(--transition);
        }

        .feature-card:hover::before {
            left: 100%;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-card i {
            font-size: 2.5rem;
            color: var(--accent);
            margin-bottom: 1rem;
        }

        .feature-card h3 {
            margin-bottom: 1rem;
            color: var(--primary);
        }

        /* Hours & Location */
        .hours-location {
            display: flex;
            justify-content: space-between;
            background-color: var(--card-bg);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px var(--shadow);
            transition: var(--transition);
        }

        .hours-location > div {
            flex: 1;
        }

        .hours-location h3 {
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .hours ul {
            list-style: none;
        }

        .hours li {
            margin-bottom: 0.5rem;
        }

        .location p {
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
        }

        .location i {
            margin-right: 10px;
            color: var(--accent);
        }

        /* About Section */
        .about-content {
            display: flex;
            align-items: center;
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .about-image {
            flex: 1;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px var(--shadow);
            transition: var(--transition);
        }

        .about-image:hover {
            transform: scale(1.02);
        }

        .about-image img {
            width: 100%;
            height: auto;
            display: block;
        }

        .about-text {
            flex: 1;
        }

        .about-text h3 {
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .about-text p {
            margin-bottom: 1rem;
        }

        /* Team Section */
        .team-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .team-member {
            background-color: var(--card-bg);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px var(--shadow);
            transition: var(--transition);
            position: relative;
        }

        .team-member:hover {
            transform: translateY(-5px);
        }

        .team-member img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            transition: var(--transition);
        }

        .team-member:hover img {
            transform: scale(1.05);
        }

        .member-info {
            padding: 1.5rem;
        }

        .member-info h3 {
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .role {
            color: var(--accent);
            font-weight: bold;
            margin-bottom: 1rem;
        }

        /* Menu Section */
        .menu-categories {
            display: flex;
            justify-content: center;
            margin-bottom: 2rem;
            flex-wrap: wrap;
            gap: 10px;
        }

        .category-btn {
            background-color: var(--card-bg);
            border: 2px solid var(--secondary);
            color: var(--primary);
            padding: 0.5rem 1.5rem;
            border-radius: 30px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
        }

        .category-btn.active {
            background-color: var(--secondary);
            color: white;
        }

        .menu-items {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }

        .menu-item {
            background-color: var(--card-bg);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px var(--shadow);
            transition: var(--transition);
            position: relative;
        }

        .menu-item:hover {
            transform: translateY(-5px);
        }

        .menu-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            transition: var(--transition);
        }

        .menu-item:hover img {
            transform: scale(1.05);
        }

        .menu-item-content {
            padding: 1.5rem;
        }

        .menu-item-title {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
        }

        .menu-item-title h3 {
            color: var(--primary);
        }

        .price {
            color: var(--accent);
            font-weight: bold;
        }

        .menu-item-popular {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: var(--accent);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        /* Cart Styles */
        .cart-icon {
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background-color: var(--accent);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .cart-modal.active {
            display: flex;
        }

        .cart-content {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 2rem;
            width: 90%;
            max-width: 600px;
            max-height: 80vh;
            overflow-y: auto;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.2);
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid #ddd;
            padding-bottom: 1rem;
        }

        .cart-items {
            margin-bottom: 1.5rem;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-controls {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .quantity-btn {
            background-color: var(--secondary);
            color: var(--primary);
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
        }

        .cart-total {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
            padding-top: 1rem;
            border-top: 1px solid #ddd;
        }

        .cart-actions {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }

        .btn-secondary {
            background-color: #6c757d;
            color: white;
        }

        .btn-secondary:hover {
            background-color: #5a6268;
        }

        /* Contact Section */
        .contact-content {
            display: flex;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .contact-info {
            flex: 1;
        }

        .contact-info-item {
            display: flex;
            align-items: flex-start;
            margin-bottom: 1.5rem;
        }

        .contact-info-item i {
            color: var(--secondary);
            font-size: 1.2rem;
            margin-right: 1rem;
            margin-top: 5px;
        }

        .contact-form {
            flex: 1;
            background-color: var(--card-bg);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px var(--shadow);
            transition: var(--transition);
        }

        .form-group {
            margin-bottom: 1.5rem;
            position: relative;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
            background-color: var(--card-bg);
            color: var(--text);
            transition: var(--transition);
        }

        .form-control:focus {
            border-color: var(--secondary);
            outline: none;
            box-shadow: 0 0 0 2px rgba(212, 184, 150, 0.3);
        }

        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }

        .map {
            border-radius: 10px;
            overflow: hidden;
            height: 300px;
            box-shadow: 0 5px 15px var(--shadow);
        }

        /* Weather Widget */
        .weather-widget {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 1.5rem;
            margin: 2rem 0;
            box-shadow: 0 5px 15px var(--shadow);
            text-align: center;
            transition: var(--transition);
        }

        .weather-widget:hover {
            transform: translateY(-5px);
        }

        .weather-info {
            display: flex;
            justify-content: space-around;
            align-items: center;
            flex-wrap: wrap;
        }

        .weather-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .temperature {
            font-size: 2rem;
            font-weight: bold;
            color: var(--accent);
        }

        .weather-details {
            text-align: left;
        }

        /* Footer */
        footer {
            background-color: var(--footer-bg);
            color: white;
            padding: 2rem 0;
            margin-top: 2rem;
            transition: var(--transition);
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
        }

        .footer-section {
            flex: 1;
            min-width: 250px;
        }

        .footer-section h3 {
            color: var(--secondary);
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }

        .footer-section p {
            margin-bottom: 1rem;
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 0.5rem;
        }

        .footer-section ul li a {
            color: white;
            text-decoration: none;
            transition: var(--transition);
            cursor: pointer;
        }

        .footer-section ul li a:hover {
            color: var(--secondary);
        }

        .social-links {
            display: flex;
            gap: 1rem;
        }

        .social-links a {
            color: white;
            font-size: 1.2rem;
            transition: var(--transition);
        }

        .social-links a:hover {
            color: var(--secondary);
        }

        .footer-bottom {
            text-align: center;
            margin-top: 2rem;
            padding-top: 1rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Scroll to Top Button */
        .scroll-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background-color: var(--secondary);
            color: var(--primary);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.5rem;
            cursor: pointer;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
            z-index: 99;
            box-shadow: 0 2px 10px var(--shadow);
        }

        .scroll-to-top.visible {
            opacity: 1;
            visibility: visible;
        }

        .scroll-to-top:hover {
            background-color: #e8d0b3;
            transform: translateY(-3px);
        }

        /* Responsive Styles */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }

            nav ul {
                margin-top: 1rem;
                flex-wrap: wrap;
                justify-content: center;
            }

            nav ul li {
                margin: 0.5rem;
            }

            .mobile-menu-btn {
                display: block;
                position: absolute;
                top: 1rem;
                right: 1rem;
            }

            .about-content,
            .contact-content,
            .hours-location {
                flex-direction: column;
            }

            .hero h1 {
                font-size: 2.2rem;
            }

            .hero p {
                font-size: 1rem;
            }

            .feature-grid,
            .team-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Animation classes */
        .fade-in {
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        // React Components for Coffee Shop Website

        // Context for global state management
        const AppContext = React.createContext();

        // Main App Component
        function App() {
            const [currentPage, setCurrentPage] = React.useState('home');
            const [darkMode, setDarkMode] = React.useState(false);
            const [cartItems, setCartItems] = React.useState([]);
            const [showCart, setShowCart] = React.useState(false);
            const [showScrollTop, setShowScrollTop] = React.useState(false);

            // Load cart from localStorage on component mount
            React.useEffect(() => {
                const savedCart = localStorage.getItem('coffeeShopCart');
                if (savedCart) {
                    setCartItems(JSON.parse(savedCart));
                }

                // Check for saved theme preference
                const savedTheme = localStorage.getItem('coffeeShopTheme');
                if (savedTheme === 'dark') {
                    setDarkMode(true);
                    document.body.classList.add('dark-mode');
                }

                // Scroll event listener
                const handleScroll = () => {
                    setShowScrollTop(window.pageYOffset > 300);
                };

                window.addEventListener('scroll', handleScroll);
                return () => window.removeEventListener('scroll', handleScroll);
            }, []);

            // Save cart to localStorage when it changes
            React.useEffect(() => {
                localStorage.setItem('coffeeShopCart', JSON.stringify(cartItems));
            }, [cartItems]);

            // Toggle dark mode
            const toggleDarkMode = () => {
                setDarkMode(!darkMode);
                if (!darkMode) {
                    document.body.classList.add('dark-mode');
                    localStorage.setItem('coffeeShopTheme', 'dark');
                } else {
                    document.body.classList.remove('dark-mode');
                    localStorage.setItem('coffeeShopTheme', 'light');
                }
            };

            // Add item to cart
            const addToCart = (item) => {
                setCartItems(prevItems => {
                    const existingItem = prevItems.find(i => i.id === item.id);
                    if (existingItem) {
                        return prevItems.map(i => 
                            i.id === item.id ? { ...i, quantity: i.quantity + 1 } : i
                        );
                    } else {
                        return [...prevItems, { ...item, quantity: 1 }];
                    }
                });
            };

            // Remove item from cart
            const removeFromCart = (id) => {
                setCartItems(prevItems => prevItems.filter(item => item.id !== id));
            };

            // Update item quantity in cart
            const updateQuantity = (id, quantity) => {
                if (quantity <= 0) {
                    removeFromCart(id);
                    return;
                }
                
                setCartItems(prevItems => 
                    prevItems.map(item => 
                        item.id === id ? { ...item, quantity } : item
                    )
                );
            };

            // Clear entire cart
            const clearCart = () => {
                setCartItems([]);
            };

            // Calculate total price
            const getTotalPrice = () => {
                return cartItems.reduce((total, item) => total + (item.price * item.quantity), 0).toFixed(2);
            };

            // Calculate total items count
            const getTotalItems = () => {
                return cartItems.reduce((total, item) => total + item.quantity, 0);
            };

            // Scroll to top function
            const scrollToTop = () => {
                window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
            };

            // Context value
            const contextValue = {
                currentPage,
                setCurrentPage,
                darkMode,
                toggleDarkMode,
                cartItems,
                addToCart,
                removeFromCart,
                updateQuantity,
                clearCart,
                getTotalPrice,
                getTotalItems,
                showCart,
                setShowCart
            };

            return (
                <AppContext.Provider value={contextValue}>
                    <div className="app">
                        <Header />
                        <main>
                            {currentPage === 'home' && <HomePage />}
                            {currentPage === 'about' && <AboutPage />}
                            {currentPage === 'menu' && <MenuPage />}
                            {currentPage === 'contact' && <ContactPage />}
                        </main>
                        <CartModal />
                        <Footer />
                        {showScrollTop && (
                            <div className="scroll-to-top visible" onClick={scrollToTop}>
                                <i className="fas fa-chevron-up"></i>
                            </div>
                        )}
                    </div>
                </AppContext.Provider>
            );
        }

        // Header Component
        function Header() {
            const { currentPage, setCurrentPage, darkMode, toggleDarkMode, getTotalItems, setShowCart } = React.useContext(AppContext);
            const [mobileMenuOpen, setMobileMenuOpen] = React.useState(false);

            const navItems = [
                { id: 'home', label: 'Home' },
                { id: 'about', label: 'About' },
                { id: 'menu', label: 'Menu' },
                { id: 'contact', label: 'Contact' }
            ];

            const toggleMobileMenu = () => {
                setMobileMenuOpen(!mobileMenuOpen);
            };

            const handleNavClick = (pageId) => {
                setCurrentPage(pageId);
                setMobileMenuOpen(false);
                window.scrollTo(0, 0);
            };

            return (
                <header>
                    <div className="container">
                        <div className="header-content">
                            <div className="logo">
                                <i className="fas fa-coffee"></i>
                                <span>Coffee Haven</span>
                            </div>
                            <button className="mobile-menu-btn" onClick={toggleMobileMenu}>
                                <i className="fas fa-bars"></i>
                            </button>
                            <nav style={{ display: mobileMenuOpen || window.innerWidth > 768 ? 'block' : 'none' }}>
                                <ul>
                                    {navItems.map(item => (
                                        <li key={item.id}>
                                            <a 
                                                className={currentPage === item.id ? 'active' : ''}
                                                onClick={() => handleNavClick(item.id)}
                                            >
                                                {item.label}
                                            </a>
                                        </li>
                                    ))}
                                </ul>
                            </nav>
                            <div className="header-controls">
                                <button className="theme-toggle" onClick={toggleDarkMode}>
                                    <i className={darkMode ? 'fas fa-sun' : 'fas fa-moon'}></i>
                                </button>
                                <div className="cart-icon" onClick={() => setShowCart(true)}>
                                    <i className="fas fa-shopping-cart"></i>
                                    <span className="cart-count">{getTotalItems()}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </header>
            );
        }

        // Home Page Component
        function HomePage() {
            const { setCurrentPage } = React.useContext(AppContext);
            
            // Floating beans animation
            React.useEffect(() => {
                const floatingBeansContainer = document.createElement('div');
                floatingBeansContainer.className = 'floating-beans';
                
                const beanCount = 15;
                for (let i = 0; i < beanCount; i++) {
                    const bean = document.createElement('div');
                    bean.className = 'bean';
                    
                    const left = Math.random() * 100;
                    const delay = Math.random() * 15;
                    const duration = 15 + Math.random() * 10;
                    const size = 10 + Math.random() * 20;
                    
                    bean.style.left = `${left}%`;
                    bean.style.animationDelay = `${delay}s`;
                    bean.style.animationDuration = `${duration}s`;
                    bean.style.width = `${size}px`;
                    bean.style.height = `${size/2}px`;
                    
                    floatingBeansContainer.appendChild(bean);
                }
                
                const heroElement = document.querySelector('.hero');
                if (heroElement) {
                    heroElement.appendChild(floatingBeansContainer);
                }
                
                return () => {
                    if (heroElement && floatingBeansContainer.parentNode === heroElement) {
                        heroElement.removeChild(floatingBeansContainer);
                    }
                };
            }, []);

            const features = [
                {
                    icon: 'fas fa-coffee',
                    title: 'Premium Quality Beans',
                    description: 'We source our coffee beans from the best regions worldwide, ensuring exceptional flavor in every cup.'
                },
                {
                    icon: 'fas fa-user-tie',
                    title: 'Expert Baristas',
                    description: 'Our skilled baristas are trained to craft the perfect coffee, customized to your preferences.'
                },
                {
                    icon: 'fas fa-couch',
                    title: 'Cozy Atmosphere',
                    description: 'Relax in our comfortable space designed for work, conversation, or simply enjoying a moment of peace.'
                }
            ];

            return (
                <section id="home" className="page fade-in">
                    <div className="hero">
                        <div className="container">
                            <h1>Welcome to Coffee Haven</h1>
                            <p>Discover the perfect brew in our cozy coffee shop. We source the finest beans from around the world and craft each cup with passion and precision.</p>
                            <button className="btn" onClick={() => setCurrentPage('menu')}>View Our Menu</button>
                        </div>
                    </div>

                    <div className="container">
                        <div className="features">
                            <h2 className="section-title">Why Choose Us</h2>
                            <div className="feature-grid">
                                {features.map((feature, index) => (
                                    <div key={index} className="feature-card">
                                        <i className={feature.icon}></i>
                                        <h3>{feature.title}</h3>
                                        <p>{feature.description}</p>
                                    </div>
                                ))}
                            </div>
                        </div>

                        <div className="hours-location">
                            <div className="hours">
                                <h3>Opening Hours</h3>
                                <ul>
                                    <li>Monday - Friday: 7am - 8pm</li>
                                    <li>Saturday: 8am - 6pm</li>
                                    <li>Sunday: 8am - 4pm</li>
                                </ul>
                            </div>
                            <div className="location">
                                <h3>Visit Us</h3>
                                <p>123 Coffee Street, Brew City, BC 12345</p>
                                <p><i className="fas fa-phone"></i> (555) 123-4567</p>
                            </div>
                        </div>
                    </div>
                </section>
            );
        }

        // About Page Component
        function AboutPage() {
            const { setCurrentPage } = React.useContext(AppContext);

            const teamMembers = [
                {
                    name: 'Michael Chen',
                    role: 'Head Barista',
                    description: 'With 8 years of experience, Michael creates coffee art that tastes as good as it looks.',
                    image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                },
                {
                    name: 'Emily Rodriguez',
                    role: 'Shop Manager',
                    description: 'Emily ensures every customer has an exceptional experience from the moment they walk in.',
                    image:'manager.jpeg'
                },
                    
                {
                    name: 'David Wilson',
                    role: 'Master Roaster',
                    description: 'David\'s expertise in roasting brings out the unique flavors in each coffee bean we source.',
                    image: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80'
                }
            ];

            return (
                <section id="about" className="page fade-in">
                    <div className="container">
                        <h2 className="section-title">Our Story</h2>
                        <div className="about-content">
                            <div className="about-image">
                                <img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80" alt="Coffee shop interior" />
                            </div>
                            <div className="about-text">
                                <h3>Brewing Excellence Since 2010</h3>
                                <p>Coffee Haven began as a small dream in a garage, where our founder, Sarah Johnson, experimented with different roasting techniques to create the perfect cup of coffee.</p>
                                <p>Today, we've grown into a beloved community hub where people gather to enjoy exceptional coffee, delicious pastries, and great conversation.</p>
                                <p>Our commitment remains the same: to serve ethically sourced, carefully roasted coffee that delights the senses and brings people together.</p>
                                <button className="btn" onClick={() => setCurrentPage('contact')}>Visit Us</button>
                            </div>
                        </div>

                        <div className="team">
                            <h2 className="section-title">Meet Our Team</h2>
                            <div className="team-grid">
                                {teamMembers.map((member, index) => (
                                    <div key={index} className="team-member">
                                        <img src={member.image} alt={member.name} />
                                        <div className="member-info">
                                            <h3>{member.name}</h3>
                                            <p className="role">{member.role}</p>
                                            <p>{member.description}</p>
                                        </div>
                                    </div>
                                ))}
                            </div>
                        </div>
                    </div>
                </section>
            );
        }

        // Menu Page Component
        function MenuPage() {
            const { addToCart } = React.useContext(AppContext);
            const [activeCategory, setActiveCategory] = React.useState('all');

            const menuItems = [
                {
                    id: 'espresso',
                    name: 'Espresso',
                    price: 800,
                    category: 'coffee',
                    description: 'A rich, concentrated coffee served in a small, strong shot.',
                    image: 'https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80',
                    popular: true
                },
                {
                    id: 'cappuccino',
                    name: 'Cappuccino',
                    price: 500,
                    category: 'coffee',
                    description: 'Equal parts espresso, steamed milk, and milk foam.',
                    image: 'https://images.unsplash.com/photo-1561047029-3000c68339ca?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                },
                {
                    id: 'latte',
                    name: 'Latte',
                    price: 750,
                    category: 'coffee',
                    description: 'Espresso with steamed milk and a light layer of foam.',
                    image: 'https://images.unsplash.com/photo-1572442388796-11668a67e53d?ixlib=rb-4.0.3&auto=format&fit=crop&w=635&q=80'
                },
                {
                    id: 'earl-grey',
                    name: 'Earl Grey',
                    price:600,
                    category: 'tea',
                    description: 'Classic black tea flavored with oil of bergamot.',
                    image: 'https://images.unsplash.com/photo-1556679343-c7306c1976bc?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                },
                {
                    id: 'chamomile',
                    name: 'Chamomile',
                    price:900,
                    category: 'tea',
                    description: 'Soothing herbal tea perfect for relaxation.',
                    image: 'https://images.unsplash.com/photo-1544787219-7f47ccb76574?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                },
                {
                    id: 'green-tea',
                    name: 'Green Tea',
                    price: 300,
                    category: 'tea',
                    description: 'Light, refreshing tea with antioxidants.',
                    image: 'https://images.unsplash.com/photo-1571934811356-5cc061b6821f?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                },
                {
                    id: 'croissant',
                    name: 'Butter Croissant',
                    price: 500,
                    category: 'pastry',
                    description: 'Flaky, buttery pastry perfect with any coffee.',
                    image: 'https://images.unsplash.com/photo-1558961363-fa8fdf82db35?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                },
                {
                    id: 'muffin',
                    name: 'Blueberry Muffin',
                    price: 500,
                    category: 'pastry',
                    description: 'Freshly baked muffin bursting with blueberries.',
                    image: 'blueberry.jpeg'
                },
                {
                    id: 'cookie',
                    name: 'Chocolate Chip Cookie',
                    price: 900,
                    category: 'pastry',
                    description: 'Classic cookie with melty chocolate chips.',
                    image: 'https://images.unsplash.com/photo-1563729784474-d77dbb933a9e?ixlib=rb-4.0.3&auto=format&fit=crop&w=634&q=80'
                }
            ];

            const categories = [
                { id: 'all', label: 'All' },
                { id: 'coffee', label: 'Coffee' },
                { id: 'tea', label: 'Tea' },
                { id: 'pastry', label: 'Pastries' }
            ];

            const filteredItems = activeCategory === 'all' 
                ? menuItems 
                : menuItems.filter(item => item.category === activeCategory);

            const handleAddToCart = (item) => {
                addToCart(item);
                
                // Visual feedback
                const button = document.querySelector(`[data-id="${item.id}"]`);
                if (button) {
                    const originalText = button.textContent;
                    button.textContent = 'Added!';
                    button.style.backgroundColor = '#28a745';
                    
                    setTimeout(() => {
                        button.textContent = originalText;
                        button.style.backgroundColor = '';
                    }, 1500);
                }
            };

            return (
                <section id="menu" className="page fade-in">
                    <div className="container">
                        <h2 className="section-title">Our Menu</h2>
                        <div className="menu-categories">
                            {categories.map(category => (
                                <button
                                    key={category.id}
                                    className={`category-btn ${activeCategory === category.id ? 'active' : ''}`}
                                    onClick={() => setActiveCategory(category.id)}
                                >
                                    {category.label}
                                </button>
                            ))}
                        </div>

                        <div className="menu-items">
                            {filteredItems.map(item => (
                                <div key={item.id} className="menu-item" data-category={item.category}>
                                    {item.popular && <span className="menu-item-popular">Popular</span>}
                                    <img src={item.image} alt={item.name} />
                                    <div className="menu-item-content">
                                        <div className="menu-item-title">
                                            <h3>{item.name}</h3>
                                            <span className="price">Rs.{item.price.toFixed(2)}</span>
                                        </div>
                                        <p>{item.description}</p>
                                        <button 
                                            className="btn btn-add-to-cart" 
                                            data-id={item.id}
                                            onClick={() => handleAddToCart(item)}
                                        >
                                            Add to Cart
                                        </button>
                                    </div>
                                </div>
                            ))}
                        </div>
                    </div>
                </section>
            );
        }

        // Contact Page Component
        function ContactPage() {
            const [weather, setWeather] = React.useState({
                temperature: '--',
                description: 'Loading weather...',
                humidity: '--',
                icon: 'fas fa-sun'
            });

            // Simulate weather API call
            React.useEffect(() => {
                const timer = setTimeout(() => {
                    setWeather({
                        temperature: 22,
                        description: 'Sunny',
                        humidity: 65,
                        icon: 'fas fa-sun'
                    });
                }, 1000);
                
                return () => clearTimeout(timer);
            }, []);

            const handleSubmit = (e) => {
                e.preventDefault();
                alert('Thank you for your message! We will get back to you soon.');
                e.target.reset();
            };

            return (
                <section id="contact" className="page fade-in">
                    <div className="container">
                        <h2 className="section-title">Get In Touch</h2>
                        
                        <div className="weather-widget">
                            <h3>Current Weather</h3>
                            <div className="weather-info">
                                <div className="weather-icon">
                                    <i className={weather.icon}></i>
                                </div>
                                <div className="temperature">
                                    <span>{weather.temperature}°C</span>
                                </div>
                                <div className="weather-details">
                                    <p>{weather.description}</p>
                                    <p>Brew City</p>
                                    <p>Humidity: {weather.humidity}%</p>
                                </div>
                            </div>
                        </div>

                        <div className="contact-content">
                            <div className="contact-info">
                                <h3>Visit Our Shop</h3>
                                <div className="contact-info-item">
                                    <i className="fas fa-map-marker-alt"></i>
                                    <div>
                                        <h4>Address</h4>
                                        <p>123 Coffee Street, Brew City, BC 12345</p>
                                    </div>
                                </div>
                                <div className="contact-info-item">
                                    <i className="fas fa-phone"></i>
                                    <div>
                                        <h4>Phone</h4>
                                        <p>(555) 123-4567</p>
                                    </div>
                                </div>
                                <div className="contact-info-item">
                                    <i className="fas fa-envelope"></i>
                                    <div>
                                        <h4>Email</h4>
                                        <p>hello@coffeehaven.com</p>
                                    </div>
                                </div>
                                <div className="contact-info-item">
                                    <i className="fas fa-clock"></i>
                                    <div>
                                        <h4>Hours</h4>
                                        <p>Monday - Friday: 7am - 8pm</p>
                                        <p>Saturday - Sunday: 8am - 6pm</p>
                                    </div>
                                </div>
                            </div>
                            <div className="contact-form">
                                <h3>Send Us a Message</h3>
                                <form onSubmit={handleSubmit}>
                                    <div className="form-group">
                                        <label htmlFor="name">Name</label>
                                        <input type="text" id="name" className="form-control" required />
                                    </div>
                                    <div className="form-group">
                                        <label htmlFor="email">Email</label>
                                        <input type="email" id="email" className="form-control" required />
                                    </div>
                                    <div className="form-group">
                                        <label htmlFor="subject">Subject</label>
                                        <input type="text" id="subject" className="form-control" required />
                                    </div>
                                    <div className="form-group">
                                        <label htmlFor="message">Message</label>
                                        <textarea id="message" className="form-control" required></textarea>
                                    </div>
                                    <button type="submit" className="btn">Send Message</button>
                                </form>
                            </div>
                        </div>
                        <div className="map">
                            <div style={{ width: '100%', height: '300px', backgroundColor: '#eee', display: 'flex', alignItems: 'center', justifyContent: 'center', borderRadius: '10px' }}>
                                <p><i className="fas fa-map-marked-alt"></i> Map would be embedded here</p>
                            </div>
                        </div>
                    </div>
                </section>
            );
        }

        // Cart Modal Component
        function CartModal() {
            const { 
                cartItems, 
                removeFromCart, 
                updateQuantity, 
                clearCart, 
                getTotalPrice, 
                showCart, 
                setShowCart 
            } = React.useContext(AppContext);

            const handleCheckout = () => {
                if (cartItems.length === 0) {
                    alert('Your cart is empty!');
                    return;
                }
                
                alert(`Thank you for your order! Total: Rs.${getTotalPrice()}`);
                clearCart();
                setShowCart(false);
            };

            const handleClose = () => {
                setShowCart(false);
            };

            if (!showCart) return null;

            return (
                <div className="cart-modal active">
                    <div className="cart-content">
                        <div className="cart-header">
                            <h2>Your Cart</h2>
                            <button className="btn btn-secondary" onClick={handleClose}>Close</button>
                        </div>
                        <div className="cart-items">
                            {cartItems.length === 0 ? (
                                <p>Your cart is empty</p>
                            ) : (
                                cartItems.map(item => (
                                    <div key={item.id} className="cart-item" data-id={item.id}>
                                        <div className="cart-item-info">
                                            <h4>{item.name}</h4>
                                            <p>${item.price.toFixed(2)}</p>
                                        </div>
                                        <div className="cart-item-controls">
                                            <button 
                                                className="quantity-btn" 
                                                onClick={() => updateQuantity(item.id, item.quantity - 1)}
                                            >
                                                -
                                            </button>
                                            <span>{item.quantity}</span>
                                            <button 
                                                className="quantity-btn" 
                                                onClick={() => updateQuantity(item.id, item.quantity + 1)}
                                            >
                                                +
                                            </button>
                                            <button 
                                                className="btn btn-secondary remove-item" 
                                                onClick={() => removeFromCart(item.id)}
                                            >
                                                Remove
                                            </button>
                                        </div>
                                    </div>
                                ))
                            )}
                        </div>
                        <div className="cart-total">
                            <span>Total:</span>
                            <span>Rs.{getTotalPrice()}</span>
                        </div>
                        <div className="cart-actions">
                            <button className="btn btn-secondary" onClick={clearCart}>Clear Cart</button>
                            <button className="btn" onClick={handleCheckout}>Checkout</button>
                        </div>
                    </div>
                </div>
            );
        }

        // Footer Component
        function Footer() {
            const { setCurrentPage } = React.useContext(AppContext);

            const handleNavClick = (pageId) => {
                setCurrentPage(pageId);
                window.scrollTo(0, 0);
            };

            const handleNewsletterSubmit = (e) => {
                e.preventDefault();
                const email = e.target.querySelector('input[type="email"]').value;
                alert(`Thank you for subscribing with ${email}! You'll receive our updates soon.`);
                e.target.reset();
            };

            return (
                <footer>
                    <div className="container">
                        <div className="footer-content">
                            <div className="footer-section">
                                <h3>Coffee Haven</h3>
                                <p>Your neighborhood coffee shop serving premium coffee, tea, and pastries in a warm, welcoming atmosphere.</p>
                                <div className="social-links">
                                    <a href="#"><i className="fab fa-facebook-f"></i></a>
                                    <a href="#"><i className="fab fa-instagram"></i></a>
                                    <a href="#"><i className="fab fa-twitter"></i></a>
                                </div>
                            </div>
                            <div className="footer-section">
                                <h3>Quick Links</h3>
                                <ul>
                                    <li><a onClick={() => handleNavClick('home')}>Home</a></li>
                                    <li><a onClick={() => handleNavClick('about')}>About</a></li>
                                    <li><a onClick={() => handleNavClick('menu')}>Menu</a></li>
                                    <li><a onClick={() => handleNavClick('contact')}>Contact</a></li>
                                </ul>
                            </div>
                            <div className="footer-section">
                                <h3>Newsletter</h3>
                                <p>Subscribe to our newsletter for updates and special offers.</p>
                                <form onSubmit={handleNewsletterSubmit}>
                                    <div className="form-group">
                                        <input type="email" className="form-control" placeholder="Your email address" required />
                                        <button type="submit" className="btn">Subscribe</button>
                                    </div>
                                </form>
                            </div>
                        </div>
                        <div className="footer-bottom">
                            <p>&copy; 2023 Coffee Haven. All rights reserved.</p>
                        </div>
                    </div>
                </footer>
            );
        }

        // Render the App
        ReactDOM.render(<App />, document.getElementById('root'));
    </script>
</body>
</html>
