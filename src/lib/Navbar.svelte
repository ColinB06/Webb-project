<nav>
    <a href="/" aria-label="Home">
        <img src="fortuna.png" alt="Fortuna Logo" />
    </a>
    <ul class="right-links">
            <li><a href="/login">Login</a></li>
            <li><a href="/register" class="btn btn-primary">Register</a></li>
    </ul>
</nav>

<style>
    /* Navbar container */
nav {
    background-color: #333; /* Background color */
    padding: 10px 20px; /* Add padding */
    display: flex; /* Make it a flex container */
    justify-content: space-between; /* Space items evenly */
    align-items: center; /* Center items vertically */
}

/* Logo styling */
nav img {
    width: 100px; /* Adjust logo width */
    height: auto; /* Maintain aspect ratio */
}

/* List styling */
.right-links {
    list-style-type: none; /* Remove default list styles */
    margin: 0; /* Remove default margin */
    padding: 0; /* Remove default padding */
}

/* List item styling */
.right-links li {
    display: inline-block; /* Display items horizontally */
    margin-left: 20px; /* Add some space between items */
}

/* Link styling */
.right-links li a {
    text-decoration: none; /* Remove underline from links */
    color: #fff; /* Link color */
    padding: 5px 10px; /* Add padding */
    border-radius: 5px; /* Add rounded corners */
    font-style: initial;
}

/* Primary button styling */
.right-links li a.btn-primary {
    background-color: #00ffb7; /* Button background color */
}

/* Hover effect for links */
.right-links li a:hover {
    background-color: #555; /* Darken background color on hover */
}

</style>