<script>
    export let hideOnSpecificPage = false;
</script>

 



<div class="sidebar" style="{hideOnSpecificPage ? 'display: none;' : ''}">
    <div class="sidebar-box">
        <p class="games-title">Pick your poison</p> 
        <ul>
            <li><a href="/coinflip"><img src="coinflip.png" alt="Coinflip" class="icon"> Coinflip</a></li>
            <li><a href="/blackjack"><img src="coinflip.png" alt="Coinflip" class="icon"> Blackjack</a></li>
        </ul>
    </div>
</div>




<style>
.sidebar {
    position: absolute;
    width: 250px;
    background-color: #333; 
    padding: 20px; 
    border-radius: 10px; 
    margin-top: 10px;
}


.sidebar-box {
    margin-bottom: 20px;
}


.games-title {
    font-size: 18px; 
    font-weight: bold; 
    margin-bottom: 10px; 
    font-style: oblique;
}


.sidebar-box ul {
    list-style-type: none; 
    padding: 0; 
    margin: 0; 
}

/* List item styling */
.sidebar-box ul li {
    margin-bottom: 10px;
}

/* Link styling */
.sidebar-box ul li a {
    text-decoration: none; 
    color: rgb(255, 255, 255);
    display: flex;
    align-items: center; 
    font-style: oblique;
}

/* Icon styling */
.icon {
    width: 20px;
    height: 20px; 
    margin-right: 10px; 
}

    </style>