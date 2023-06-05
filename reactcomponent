<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
<script src="https://cdn.finsweet.com/files/cmslibrary-v1.8.js"></script>



<script>
  
  
(function() {
	// create a new Library instance and store it in a variable called "projectsGrid"
	var projectsGrid = new FsLibrary('.filter-collection-list')
      var myFilters = [
      {
          filterWrapper: ".filters-wrapper",
          filterType: "exclusive",
          filterByClass: ".categ" 
      }
	]
      
 	// run filter on our instance
	projectsGrid.filter({
		filterArray: myFilters, // the filter group name we defined
    	activeClass: 'fltr-active', // the active class we give to our buttons
		animation: {
		enable: true,
		duration: 300,
		easing: 'ease-out',
		effects: 'fade translate(0px,20px)'
		}
  	})
  

  /* LOAD MORE COMPONENT */
  
	// run loadmore on our instance
 /*projectsGrid.loadmore({
	button: ".load-more-button",
    loadAll: true,
    resetIx: true,
    infiniteScroll: true,
    infiniteScrollPercent: 70,
	animation: {
      enable: false,
    }

	})
 
*/
 
    
 //pagination
 projectsGrid.loadmore({
	button: ".load-more-button",
    resetIx: true,
    loadAll: true,
    paginate: {
			enable: true,
			itemsPerPage: 6,
			insertPagination: '.pagination-container',
			bgColor: '#FFFFFF',
			bgColorActive: '#7757ff',
			textColor: '#000000',
      textColorActive: '#FFFFFF',
			borderColor: '#3D315B'
    },
		animation: {
			enable: false
    }
	})



})();
</script>


<script>
  
$(document).ready(function($){
  
  	 
   //home page knowledgebase filter select default 1st one
   
  
   

  
  
  
  
  
  if($(".hover-link-wrapper.newgap").length){

    $(window).scroll(function() {  
        if($(window).scrollTop() >= $('.filter-collection-sec').offset().top + $('.filter-collection-sec').outerHeight() - window.innerHeight) {
            $(".hover-link-wrapper.newgap").removeClass("show");   
        }
        else if($(window).scrollTop() <= $('.filter-collection-sec').offset().top)
        {
        $(".hover-link-wrapper.newgap").removeClass("show"); 
        }
        else{
        $(".hover-link-wrapper.newgap").addClass("show"); 
        }
    });
  }
  
  
  
  

  
  

  
})



</script>




<script>
$(function () {

  var hasAlreadyCookies = getCookie('cookie-consent-preferences');
  var allCriteria = ["Essential Trigger", "Analytics Trigger"]

  console.log(hasAlreadyCookies)
  	
  //if someone hasn't the cookie conset thing 
  if (hasAlreadyCookies === null) {
    console.log("no cookies")
    
    $('#cookies-wrapper-all').show()
    $('#cookie-popup').show()
    $('#cookie-allow-all').click(function(){ allowAllCookies() })

    //define vars
    var selected = [];
    var formID = "#wf-form-cookie-form";

    //update input fields when changing value
    var update = function () {
      selected = []
      $(formID + " input:checked").each(function(){
        var attribute = $(this).attr('cookie-cat')
        selected.push(attribute)
      });
      console.log("form result", selected);
    };
    update();
    $(formID).change(update);

    //when form is submitted
    $(formID).on("submit", function (e) {
      //prevent reload
      e.preventDefault();
      console.log(selected.length);
      //check if tracking is enabled
      selected.forEach(function (category) {
        dataLayer.push({
          event: "userPrefUpdate",
          cookieAccepted: category,
        });
      })

      setCookie('cookie-consent-preferences', selected, 365)

      $('#cookie-popup').hide()
      $('#cookie-popup-wrapper').hide()

      return false;
    });
  }else{

    var array = hasAlreadyCookies.split(',');
    array.forEach(function (category) {
      dataLayer.push({
        event: "userPrefUpdate",
        cookieAccepted: category,
      });
    })
    
    //hide popup banner and preferences
    $('#cookie-popup').hide()
    $('#cookie-popup-wrapper').hide()
  }


  //allow all 
  function allowAllCookies(){
    $('#cookie-popup').hide()
    
    allCriteria.forEach(function (category){
      dataLayer.push({
        event: "userPrefUpdate",
        cookieAccepted: category,
      });
    })
    setCookie('cookie-consent-preferences', allCriteria, 365)
  }

  //set cookies
  function setCookie(name,value,days) {
    var expires = "";
    if (days) {
        var date = new Date();
        date.setTime(date.getTime() + (days*24*60*60*1000));
        expires = "; expires=" + date.toUTCString();
    }
    document.cookie = name + "=" + (value || "")  + expires + "; path=/";
  }

  //get cookies
  function getCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');
    for(var i=0;i < ca.length;i++) {
        var c = ca[i];
        while (c.charAt(0)==' ') c = c.substring(1,c.length);
        if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    }
    return null;
  }
});

</script>
