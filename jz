/* JS Document */

/******************************

[Table of Contents]

1. Vars and Inits
2. Set Header
3. Init Custom Dropdown
4. Init Page Menu
5. Init Deals Slider
6. Init Tab Lines
7. Init Tabs
8. Init Featured Slider
9. Init Favorites
10. Init ZIndex
11. Init Popular Categories Slider
12. Init Banner 2 Slider
13. Init Arrivals Slider
14. Init Arrivals Slider ZIndex
15. Init Best Sellers Slider
16. Init Trends Slider



******************************/

$(document).ready(function()
{
	"use strict";

	/* 

	1. Vars and Inits

	*/

	var menuActive = false;
	var header = $('.header');

	setHeader();

	initCustomDropdown();
	initPageMenu();
	initDealsSlider();
	initTabLines();
	initFeaturedSlider();
	featuredSliderZIndex();
	initPopularSlider();
	initBanner2Slider();
	initFavs();
	initArrivalsSlider();
	arrivalsSliderZIndex();
	bestsellersSlider();
	initTabs();
	initTrendsSlider();
	;

	$(window).on('resize', function()
	{
		setHeader();
		featuredSliderZIndex();
		initTabLines();
	});

	/* 

	2. Set Header

	*/

	function setHeader()
	{
		//To pin main nav to the top of the page when it's reached
		//uncomment the following

		// var controller = new ScrollMagic.Controller(
		// {
		// 	globalSceneOptions:
		// 	{
		// 		triggerHook: 'onLeave'
		// 	}
		// });

		// var pin = new ScrollMagic.Scene(
		// {
		// 	triggerElement: '.main_nav'
		// })
		// .setPin('.main_nav').addTo(controller);

		if(window.innerWidth > 991 && menuActive)
		{
			closeMenu();
		}
	}

	/* 

	3. Init Custom Dropdown

	*/

	function initCustomDropdown()
	{
		if($('.custom_dropdown_placeholder').length && $('.custom_list').length)
		{
			var placeholder = $('.custom_dropdown_placeholder');
			var list = $('.custom_list');
		}

		placeholder.on('click', function (ev)
		{
			if(list.hasClass('active'))
			{
				list.removeClass('active');
			}
			else
			{
				list.addClass('active');
			}

			$(document).one('click', function closeForm(e)
			{
				if($(e.target).hasClass('clc'))
				{
					$(document).one('click', closeForm);
				}
				else
				{
					list.removeClass('active');
				}
			});

		});

		$('.custom_list a').on('click', function (ev)
		{
			ev.preventDefault();
			var index = $(this).parent().index();

			placeholder.text( $(this).text() ).css('opacity', '1');

			if(list.hasClass('active'))
			{
				list.removeClass('active');
			}
			else
			{
				list.addClass('active');
			}
		});


		$('select').on('change', function (e)
		{
			placeholder.text(this.value);

			$(this).animate({width: placeholder.width() + 'px' });
		});
	}

	/* 

	4. Init Page Menu

	*/
	function initPageMenu()
	{
		if($('.page_menu').length && $('.page_menu_content').length)
		{
			var menu = $('.page_menu');
			var menuContent = $('.page_menu_content');
			var menuTrigger = $('.menu_trigger');

			//Open / close page menu
			menuTrigger.on('click', function()
			{
				if(!menuActive)
				{
					openMenu();
				}
				else
				{
					closeMenu();
				}
			});

			//Handle page menu
			if($('.page_menu_item').length)
			{
				var items = $('.page_menu_item');
				items.each(function()
				{
					var item = $(this);
					if(item.hasClass("has-children"))
					{
						item.on('click', function(evt)
						{
							evt.preventDefault();
							evt.stopPropagation();
							var subItem = item.find('> ul');
						    if(subItem.hasClass('active'))
						    {
						    	subItem.toggleClass('active');
								TweenMax.to(subItem, 0.3, {height:0});
						    }
						    else
						    {
						    	subItem.toggleClass('active');
						    	TweenMax.set(subItem, {height:"auto"});
								TweenMax.from(subItem, 0.3, {height:0});
						    }
						});
					}
				});
			}
		}
	}

	function openMenu()
	{
		var menu = $('.page_menu');
		var menuContent = $('.page_menu_content');
		TweenMax.set(menuContent, {height:"auto"});
		TweenMax.from(menuContent, 0.3, {height:0});
		menuActive = true;
	}

	function closeMenu()
	{
		var menu = $('.page_menu');
		var menuContent = $('.page_menu_content');
		TweenMax.to(menuContent, 0.3, {height:0});
		menuActive = false;
	}

	/* 

	5. Init Deals Slider

	*/

	function initDealsSlider()
	{
		if($('.deals_slider').length)
		{
			var dealsSlider = $('.deals_slider');
			dealsSlider.owlCarousel(
			{
				items:1,
				loop:false,
				navClass:['deals_slider_prev', 'deals_slider_next'],
				nav:false,
				dots:false,
				smartSpeed:1200,
				margin:30,
				autoplay:false,
				autoplayTimeout:5000
			});

			if($('.deals_slider_prev').length)
			{
				var prev = $('.deals_slider_prev');
				prev.on('click', function()
				{
					dealsSlider.trigger('prev.owl.carousel');
				});	
			}

			if($('.deals_slider_next').length)
			{
				var next = $('.deals_slider_next');
				next.on('click', function()
				{
					dealsSlider.trigger('next.owl.carousel');
				});	
			}
		}
	}

	/* 

	6. Init Tab Lines

	*/

	function initTabLines()
	{
		if($('.tabs').length)
		{
			var tabs = $('.tabs');

			tabs.each(function()
			{
				var tabsItem = $(this);
				var tabsLine = tabsItem.find('.tabs_line span');
				var tabGroup = tabsItem.find('ul li');

				var posX = $(tabGroup[0]).position().left;
				tabsLine.css({'left': posX, 'width': $(tabGroup[0]).width()});
				tabGroup.each(function()
				{
					var tab = $(this);
					tab.on('click', function()
					{
						if(!tab.hasClass('active'))
						{
							tabGroup.removeClass('active');
							tab.toggleClass('active');
							var tabXPos = tab.position().left;
							var tabWidth = tab.width();
							tabsLine.css({'left': tabXPos, 'width': tabWidth});
						}
					});
				});
			});
		}
	}

	/* 

	7. Init Tabs

	*/

	function initTabs()
	{
		if($('.tabbed_container').length)
		{
			//Handle tabs switching

			var tabsContainers = $('.tabbed_container');
			tabsContainers.each(function()
			{
				var tabContainer = $(this);
				var tabs = tabContainer.find('.tabs ul li');
				var panels = tabContainer.find('.panel');
				var sliders = panels.find('.slider');

				tabs.each(function()
				{
					var tab = $(this);
					tab.on('click', function()
					{
						panels.removeClass('active');
						var tabIndex = tabs.index(this);
						$($(panels[tabIndex]).addClass('active'));
						sliders.slick("unslick");
						sliders.each(function()
						{
							var slider = $(this);
							// slider.slick("unslick");
							if(slider.hasClass('bestsellers_slider'))
							{
								initBSSlider(slider);
							}
							if(slider.hasClass('featured_slider'))
							{
								initFSlider(slider);
							}
							if(slider.hasClass('arrivals_slider'))
							{
								initASlider(slider);
							}
						});
					});	
				});
			});
		}
	}

	/* 

	8. Init Featured Slider

	*/

	function initFeaturedSlider()
	{
		if($('.featured_slider').length)
		{
			var featuredSliders = $('.featured_slider');
			featuredSliders.each(function()
			{
				var featuredSlider = $(this);
				initFSlider(featuredSlider);
			});
				
		}
	}

	function initFSlider(fs)
	{
		var featuredSlider = fs;
		featuredSlider.on('init', function()
		{
			var activeItems = featuredSlider.find('.slick-slide.slick-active');
			for(var x = 0; x < activeItems.length - 1; x++)
			{
				var item = $(activeItems[x]);
				item.find('.border_active').removeClass('active');
				if(item.hasClass('slick-active'))
				{
					item.find('.border_active').addClass('active');
				}
			}
		}).on(
		{
			afterChange: function(event, slick, current_slide_index, next_slide_index)
			{
				var activeItems = featuredSlider.find('.slick-slide.slick-active');
				activeItems.find('.border_active').removeClass('active');
				for(var x = 0; x < activeItems.length - 1; x++)
				{
					var item = $(activeItems[x]);
					item.find('.border_active').removeClass('active');
					if(item.hasClass('slick-active'))
					{
						item.find('.border_active').addClass('active');
					}
				}
			}
		})
		.slick(
		{
			rows:2,
			slidesToShow:4,
			slidesToScroll:4,
			infinite:false,
			arrows:false,
			dots:true,
			responsive:
			[
				{
					breakpoint:768, settings:
					{
						rows:2,
						slidesToShow:3,
						slidesToScroll:3,
						dots:true
					}
				},
				{
					breakpoint:575, settings:
					{
						rows:2,
						slidesToShow:2,
						slidesToScroll:2,
						dots:false
					}
				},
				{
					breakpoint:480, settings:
					{
						rows:1,
						slidesToShow:1,
						slidesToScroll:1,
						dots:false
					}
				}
			]
		});
	}

	/* 

	9. Init Favorites

	*/

	function initFavs()
	{
		// Handle Favorites
		var items = document.getElementsByClassName('product_fav');
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('click', function(fn)
			{
				fn.target.classList.toggle('active');
			});
		}
	}

	/* 

	10. Init ZIndex

	*/

	function featuredSliderZIndex()
	{
		// Hide slider dots on item hover
		var items = document.getElementsByClassName('featured_slider_item');
		
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('mouseenter', function()
			{
				$('.featured_slider .slick-dots').css('display', "none");
			});

			item.addEventListener('mouseleave', function()
			{
				$('.featured_slider .slick-dots').css('display', "block");
			});
		}
	}
		/* 

	11. Init Popular Categories Slider

	*/

	function initPopularSlider()
	{
		if($('.popular_categories_slider').length)
		{
			var popularSlider = $('.popular_categories_slider');

			popularSlider.owlCarousel(
			{
				loop:true,
				autoplay:false,
				nav:false,
				dots:false,
				responsive:
				{
					0:{items:1},
					575:{items:2},
					640:{items:3},
					768:{items:4},
					991:{items:5}
				}
			});

			if($('.popular_categories_prev').length)
			{
				var prev = $('.popular_categories_prev');
				prev.on('click', function()
				{
					popularSlider.trigger('prev.owl.carousel');
				});
			}

			if($('.popular_categories_next').length)
			{
				var next = $('.popular_categories_next');
				next.on('click', function()
				{
					popularSlider.trigger('next.owl.carousel');
				});
			}
		}
	}

	/* 

	12. Init Banner 2 Slider

	*/

	function initBanner2Slider()
	{
		if($('.banner_2_slider').length)
		{
			var banner2Slider = $('.banner_2_slider');
			banner2Slider.owlCarousel(
			{
				items:1,
				loop:true,
				nav:false,
				dots:true,
				dotsContainer: '.banner_2_dots',
				smartSpeed:1200
			});
		}
	}

	/* 

	13. Init Arrivals Slider

	*/

	function initArrivalsSlider()
	{
		if($('.arrivals_slider').length)
		{
			var arrivalsSliders = $('.arrivals_slider');
			arrivalsSliders.each(function()
			{
				var arrivalsSlider = $(this);
				initASlider(arrivalsSlider);
			});	
			
		}
	}

	function initASlider(as)
	{
		var arrivalsSlider = as;
		arrivalsSlider.on('init', function()
		{
			var activeItems = arrivalsSlider.find('.slick-slide.slick-active');
			for(var x = 0; x < activeItems.length - 1; x++)
			{
				var item = $(activeItems[x]);
				item.find('.border_active').removeClass('active');
				if(item.hasClass('slick-active'))
				{
					item.find('.border_active').addClass('active');
				}
			}
		}).on(
		{
			afterChange: function(event, slick, current_slide_index, next_slide_index)
			{
				var activeItems = arrivalsSlider.find('.slick-slide.slick-active');
				activeItems.find('.border_active').removeClass('active');
				for(var x = 0; x < activeItems.length - 1; x++)
				{
					var item = $(activeItems[x]);
					item.find('.border_active').removeClass('active');
					if(item.hasClass('slick-active'))
					{
						item.find('.border_active').addClass('active');
					}
				}
			}
		})
		.slick(
		{
			rows:2,
			slidesToShow:5,
			slidesToScroll:5,
			infinite:false,
			arrows:false,
			dots:true,
			responsive:
			[
				{
					breakpoint:768, settings:
					{
						rows:2,
						slidesToShow:3,
						slidesToScroll:3,
						dots:true
					}
				},
				{
					breakpoint:575, settings:
					{
						rows:2,
						slidesToShow:2,
						slidesToScroll:2,
						dots:false
					}
				},
				{
					breakpoint:480, settings:
					{
						rows:1,
						slidesToShow:1,
						slidesToScroll:1,
						dots:false
					}
				}
			]
		});
	}

	/* 

	14. Init Arrivals Slider ZIndex

	*/

	function arrivalsSliderZIndex()
	{
		// Hide slider dots on item hover
		var items = document.getElementsByClassName('arrivals_slider_item');
		
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('mouseenter', function()
			{
				$('.arrivals_slider .slick-dots').css('display', "none");
			});

			item.addEventListener('mouseleave', function()
			{
				$('.arrivals_slider .slick-dots').css('display', "block");
			});
		}
	}

	/* 

	15. Init Best Sellers Slider

	*/

	function bestsellersSlider()
	{
		if($('.bestsellers_slider').length)
		{
			var bestsellersSliders = $('.bestsellers_slider');
			bestsellersSliders.each(function()
			{
				var bestsellersSlider = $(this);

				initBSSlider(bestsellersSlider);
			})	
		}
	}

	function initBSSlider(bss)
	{
		var bestsellersSlider = bss;

		bestsellersSlider.slick(
		{
			rows:2,
			infinite:true,
			slidesToShow:3,
			slidesToScroll:3,
			arrows:false,
			dots:true,
			autoplay: true,
  			autoplaySpeed: 6000,
			responsive:
			[
				{
					breakpoint:1199, settings:
					{
						rows:2,
						slidesToShow:2,
						slidesToScroll:2,
						dots:true
					}
				},
				{
					breakpoint:991, settings:
					{
						rows:2,
						slidesToShow:1,
						slidesToScroll:1,
						dots:true
					}
				},
				{
					breakpoint:575, settings:
					{
						rows:1,
						slidesToShow:1,
						slidesToScroll:1,
						dots:false
					}
				}
			]
		});
	}

	/* 

	16. Init Trends Slider

	*/

	function initTrendsSlider()
	{
		if($('.trends_slider').length)
		{
			var trendsSlider = $('.trends_slider');
			trendsSlider.owlCarousel(
			{
				loop:false,
				margin:30,
				nav:false,
				dots:false,
				autoplayHoverPause:true,
				autoplay:false,
				responsive:
				{
					0:{items:1},
					575:{items:2},
					991:{items:3}
				}
			});

			trendsSlider.on('click', '.trends_fav', function (ev)
			{
			    $(ev.target).toggleClass('active');
			});

			if($('.trends_prev').length)
			{
				var prev = $('.trends_prev');
				prev.on('click', function()
				{
					trendsSlider.trigger('prev.owl.carousel');
				});
			}

			if($('.trends_next').length)
			{
				var next = $('.trends_next');
				next.on('click', function()
				{
					trendsSlider.trigger('next.owl.carousel');
				});
			}
		}
	}
});
/* JS Document */

/******************************

[Table of Contents]

1. Vars and Inits
2. Set Header
3. Init Menu
4. Init Favorite
5. Init Fix Product Border
6. Init Isotope Filtering
7. Init Price Slider
8. Init Checkboxes



******************************/

jQuery(document).ready(function($)
{
	"use strict";

	/* 

	1. Vars and Inits

	*/

	var header = $('.header');
	var topNav = $('.top_nav')
	var mainSlider = $('.main_slider');
	var hamburger = $('.hamburger_container');
	var menu = $('.hamburger_menu');
	var menuActive = false;
	var hamburgerClose = $('.hamburger_close');
	var fsOverlay = $('.fs_menu_overlay');

	setHeader();

	$(window).on('resize', function()
	{
		initFixProductBorder();
		setHeader();
	});

	$(document).on('scroll', function()
	{
		setHeader();
	});

	initMenu();
	initFavorite();
	initFixProductBorder();
	initIsotopeFiltering();
	initPriceSlider();
	initCheckboxes();

	/* 

	2. Set Header

	*/

	function setHeader()
	{
		if(window.innerWidth < 992)
		{
			if($(window).scrollTop() > 100)
			{
				header.css({'top':"0"});
			}
			else
			{
				header.css({'top':"0"});
			}
		}
		else
		{
			if($(window).scrollTop() > 100)
			{
				header.css({'top':"-50px"});
			}
			else
			{
				header.css({'top':"0"});
			}
		}
		if(window.innerWidth > 991 && menuActive)
		{
			closeMenu();
		}
	}

	/* 

	3. Init Menu

	*/

	function initMenu()
	{
		if(hamburger.length)
		{
			hamburger.on('click', function()
			{
				if(!menuActive)
				{
					openMenu();
				}
			});
		}

		if(fsOverlay.length)
		{
			fsOverlay.on('click', function()
			{
				if(menuActive)
				{
					closeMenu();
				}
			});
		}

		if(hamburgerClose.length)
		{
			hamburgerClose.on('click', function()
			{
				if(menuActive)
				{
					closeMenu();
				}
			});
		}

		if($('.menu_item').length)
		{
			var items = document.getElementsByClassName('menu_item');
			var i;

			for(i = 0; i < items.length; i++)
			{
				if(items[i].classList.contains("has-children"))
				{
					items[i].onclick = function()
					{
						this.classList.toggle("active");
						var panel = this.children[1];
					    if(panel.style.maxHeight)
					    {
					    	panel.style.maxHeight = null;
					    }
					    else
					    {
					    	panel.style.maxHeight = panel.scrollHeight + "px";
					    }
					}
				}	
			}
		}
	}

	function openMenu()
	{
		menu.addClass('active');
		// menu.css('right', "0");
		fsOverlay.css('pointer-events', "auto");
		menuActive = true;
	}

	function closeMenu()
	{
		menu.removeClass('active');
		fsOverlay.css('pointer-events', "none");
		menuActive = false;
	}

	/* 

	4. Init Favorite

	*/

    function initFavorite()
    {
    	if($('.favorite').length)
    	{
    		var favs = $('.favorite');

    		favs.each(function()
    		{
    			var fav = $(this);
    			var active = false;
    			if(fav.hasClass('active'))
    			{
    				active = true;
    			}

    			fav.on('click', function()
    			{
    				if(active)
    				{
    					fav.removeClass('active');
    					active = false;
    				}
    				else
    				{
    					fav.addClass('active');
    					active = true;
    				}
    			});
    		});
    	}
    }

    /* 

	5. Init Fix Product Border

	*/

    function initFixProductBorder()
    {
    	if($('.product_filter').length)
    	{
			var products = $('.product_filter:visible');
    		var wdth = window.innerWidth;

    		// reset border
    		products.each(function()
    		{
    			$(this).css('border-right', 'solid 1px #e9e9e9');
    		});

    		// if window width is 991px or less

    		if(wdth < 480)
			{
				for(var i = 0; i < products.length; i++)
				{
					var product = $(products[i]);
					product.css('border-right', 'none');
				}
			}

    		else if(wdth < 576)
			{
				if(products.length < 5)
				{
					var product = $(products[products.length - 1]);
					product.css('border-right', 'none');
				}
				for(var i = 1; i < products.length; i+=2)
				{
					var product = $(products[i]);
					product.css('border-right', 'none');
				}
			}

    		else if(wdth < 768)
			{
				if(products.length < 5)
				{
					var product = $(products[products.length - 1]);
					product.css('border-right', 'none');
				}
				for(var i = 2; i < products.length; i+=3)
				{
					var product = $(products[i]);
					product.css('border-right', 'none');
				}
			}

    		else if(wdth < 992)
			{
				if(products.length < 5)
				{
					var product = $(products[products.length - 1]);
					product.css('border-right', 'none');
				}
				for(var i = 2; i < products.length; i+=3)
				{
					var product = $(products[i]);
					product.css('border-right', 'none');
				}
			}

			//if window width is larger than 991px
			else
			{
				if(products.length < 5)
				{
					var product = $(products[products.length - 1]);
					product.css('border-right', 'none');
				}
				for(var i = 3; i < products.length; i+=4)
				{
					var product = $(products[i]);
					product.css('border-right', 'none');
				}
			}	
    	}
    }

    /* 

	6. Init Isotope Filtering

	*/

    function initIsotopeFiltering()
    {
    	var sortTypes = $('.type_sorting_btn');
    	var sortNums = $('.num_sorting_btn');
    	var sortTypesSelected = $('.sorting_type .item_sorting_btn is-checked span');
    	var filterButton = $('.filter_button');

    	if($('.product-grid').length)
    	{
    		$('.product-grid').isotope({
    			itemSelector: '.product-item',
	            getSortData: {
	            	price: function(itemElement)
	            	{
	            		var priceEle = $(itemElement).find('.product_price').text().replace( '$', '' );
	            		return parseFloat(priceEle);
	            	},
	            	name: '.product_name'
	            },
	            animationOptions: {
	                duration: 750,
	                easing: 'linear',
	                queue: false
	            }
	        });

    		// Short based on the value from the sorting_type dropdown
	        sortTypes.each(function()
	        {
	        	$(this).on('click', function()
	        	{
	        		$('.type_sorting_text').text($(this).text());
	        		var option = $(this).attr('data-isotope-option');
	        		option = JSON.parse( option );
    				$('.product-grid').isotope( option );
	        	});
	        });

	        // Show only a selected number of items
	        sortNums.each(function()
	        {
	        	$(this).on('click', function()
	        	{
	        		var numSortingText = $(this).text();
					var numFilter = ':nth-child(-n+' + numSortingText + ')';
	        		$('.num_sorting_text').text($(this).text());
    				$('.product-grid').isotope({filter: numFilter });
	        	});
	        });	

	        // Filter based on the price range slider
	        filterButton.on('click', function()
	        {
	        	$('.product-grid').isotope({
		            filter: function()
		            {
		            	var priceRange = $('#amount').val();
			        	var priceMin = parseFloat(priceRange.split('-')[0].replace('$', ''));
			        	var priceMax = parseFloat(priceRange.split('-')[1].replace('$', ''));
			        	var itemPrice = $(this).find('.product_price').clone().children().remove().end().text().replace( '$', '' );

			        	return (itemPrice > priceMin) && (itemPrice < priceMax);
		            },
		            animationOptions: {
		                duration: 750,
		                easing: 'linear',
		                queue: false
		            }
		        });
	        });
    	}
    }

    /* 

	7. Init Price Slider

	*/

    function initPriceSlider()
    {
		$( "#slider-range" ).slider(
		{
			range: true,
			min: 0,
			max: 1000,
			values: [ 0, 580 ],
			slide: function( event, ui )
			{
				$( "#amount" ).val( "$" + ui.values[ 0 ] + " - $" + ui.values[ 1 ] );
			}
		});
			
		$( "#amount" ).val( "$" + $( "#slider-range" ).slider( "values", 0 ) + " - $" + $( "#slider-range" ).slider( "values", 1 ) );
    }

    /* 

	8. Init Checkboxes

	*/

    function initCheckboxes()
    {
    	if($('.checkboxes li').length)
    	{
    		var boxes = $('.checkboxes li');

    		boxes.each(function()
    		{
    			var box = $(this);

    			box.on('click', function()
    			{
    				if(box.hasClass('active'))
    				{
    					box.find('i').removeClass('fa-square');
    					box.find('i').addClass('fa-square-o');
    					box.toggleClass('active');
    				}
    				else
    				{
    					box.find('i').removeClass('fa-square-o');
    					box.find('i').addClass('fa-square');
    					box.toggleClass('active');
    				}
    				// box.toggleClass('active');
    			});
    		});

    		if($('.show_more').length)
    		{
    			var checkboxes = $('.checkboxes');

    			$('.show_more').on('click', function()
    			{
    				checkboxes.toggleClass('active');
    			});
    		}
    	};
    }
});
/* JS Document */

/******************************

[Table of Contents]

1. Vars and Inits
2. Set Header
3. Init Custom Dropdown
4. Init Page Menu
5. Init Recently Viewed Slider
6. Init Brands Slider
7. Init Isotope
8. Init Price Slider
9. Init Favorites


******************************/

$(document).ready(function()
{
	"use strict";

	/* 

	1. Vars and Inits

	*/

	var menuActive = false;
	var header = $('.header');

	setHeader();

	initCustomDropdown();
	initPageMenu();
	initViewedSlider();
	initBrandsSlider();
	initIsotope();
	initPriceSlider();
	initFavs();

	$(window).on('resize', function()
	{
		setHeader();
	});

	/* 

	2. Set Header

	*/

	function setHeader()
	{
		//To pin main nav to the top of the page when it's reached
		//uncomment the following

		// var controller = new ScrollMagic.Controller(
		// {
		// 	globalSceneOptions:
		// 	{
		// 		triggerHook: 'onLeave'
		// 	}
		// });

		// var pin = new ScrollMagic.Scene(
		// {
		// 	triggerElement: '.main_nav'
		// })
		// .setPin('.main_nav').addTo(controller);

		if(window.innerWidth > 991 && menuActive)
		{
			closeMenu();
		}
	}

	/* 

	3. Init Custom Dropdown

	*/

	function initCustomDropdown()
	{
		if($('.custom_dropdown_placeholder').length && $('.custom_list').length)
		{
			var placeholder = $('.custom_dropdown_placeholder');
			var list = $('.custom_list');
		}

		placeholder.on('click', function (ev)
		{
			if(list.hasClass('active'))
			{
				list.removeClass('active');
			}
			else
			{
				list.addClass('active');
			}

			$(document).one('click', function closeForm(e)
			{
				if($(e.target).hasClass('clc'))
				{
					$(document).one('click', closeForm);
				}
				else
				{
					list.removeClass('active');
				}
			});

		});

		$('.custom_list a').on('click', function (ev)
		{
			ev.preventDefault();
			var index = $(this).parent().index();

			placeholder.text( $(this).text() ).css('opacity', '1');

			if(list.hasClass('active'))
			{
				list.removeClass('active');
			}
			else
			{
				list.addClass('active');
			}
		});


		$('select').on('change', function (e)
		{
			placeholder.text(this.value);

			$(this).animate({width: placeholder.width() + 'px' });
		});
	}

	/* 

	4. Init Page Menu

	*/

	function initPageMenu()
	{
		if($('.page_menu').length && $('.page_menu_content').length)
		{
			var menu = $('.page_menu');
			var menuContent = $('.page_menu_content');
			var menuTrigger = $('.menu_trigger');

			//Open / close page menu
			menuTrigger.on('click', function()
			{
				if(!menuActive)
				{
					openMenu();
				}
				else
				{
					closeMenu();
				}
			});

			//Handle page menu
			if($('.page_menu_item').length)
			{
				var items = $('.page_menu_item');
				items.each(function()
				{
					var item = $(this);
					if(item.hasClass("has-children"))
					{
						item.on('click', function(evt)
						{
							evt.preventDefault();
							evt.stopPropagation();
							var subItem = item.find('> ul');
						    if(subItem.hasClass('active'))
						    {
						    	subItem.toggleClass('active');
								TweenMax.to(subItem, 0.3, {height:0});
						    }
						    else
						    {
						    	subItem.toggleClass('active');
						    	TweenMax.set(subItem, {height:"auto"});
								TweenMax.from(subItem, 0.3, {height:0});
						    }
						});
					}
				});
			}
		}
	}

	function openMenu()
	{
		var menu = $('.page_menu');
		var menuContent = $('.page_menu_content');
		TweenMax.set(menuContent, {height:"auto"});
		TweenMax.from(menuContent, 0.3, {height:0});
		menuActive = true;
	}

	function closeMenu()
	{
		var menu = $('.page_menu');
		var menuContent = $('.page_menu_content');
		TweenMax.to(menuContent, 0.3, {height:0});
		menuActive = false;
	}

	/* 

	5. Init Recently Viewed Slider

	*/

	function initViewedSlider()
	{
		if($('.viewed_slider').length)
		{
			var viewedSlider = $('.viewed_slider');

			viewedSlider.owlCarousel(
			{
				loop:true,
				margin:30,
				autoplay:true,
				autoplayTimeout:6000,
				nav:false,
				dots:false,
				responsive:
				{
					0:{items:1},
					575:{items:2},
					768:{items:3},
					991:{items:4},
					1199:{items:6}
				}
			});

			if($('.viewed_prev').length)
			{
				var prev = $('.viewed_prev');
				prev.on('click', function()
				{
					viewedSlider.trigger('prev.owl.carousel');
				});
			}

			if($('.viewed_next').length)
			{
				var next = $('.viewed_next');
				next.on('click', function()
				{
					viewedSlider.trigger('next.owl.carousel');
				});
			}
		}
	}

	/* 

	6. Init Brands Slider

	*/

	function initBrandsSlider()
	{
		if($('.brands_slider').length)
		{
			var brandsSlider = $('.brands_slider');

			brandsSlider.owlCarousel(
			{
				loop:true,
				autoplay:true,
				autoplayTimeout:5000,
				nav:false,
				dots:false,
				autoWidth:true,
				items:8,
				margin:42
			});

			if($('.brands_prev').length)
			{
				var prev = $('.brands_prev');
				prev.on('click', function()
				{
					brandsSlider.trigger('prev.owl.carousel');
				});
			}

			if($('.brands_next').length)
			{
				var next = $('.brands_next');
				next.on('click', function()
				{
					brandsSlider.trigger('next.owl.carousel');
				});
			}
		}
	}

	/* 

	7. Init Isotope

	*/

	function initIsotope()
	{
		var sortingButtons = $('.shop_sorting_button');

		$('.product_grid').isotope({
			itemSelector: '.product_item',
            getSortData: {
            	price: function(itemElement)
            	{
            		var priceEle = $(itemElement).find('.product_price').text().replace( '$', '' );
            		return parseFloat(priceEle);
            	},
            	name: '.product_name div a'
            },
            animationOptions: {
                duration: 750,
                easing: 'linear',
                queue: false
            }
        });

        // Sort based on the value from the sorting_type dropdown
        sortingButtons.each(function()
        {
        	$(this).on('click', function()
        	{
        		$('.sorting_text').text($(this).text());
        		var option = $(this).attr('data-isotope-option');
        		option = JSON.parse(option);
				$('.product_grid').isotope(option);
        	});
        });

	}

	 /* 

	8. Init Price Slider

	*/

    function initPriceSlider()
    {
    	if($("#slider-range").length)
    	{
    		$("#slider-range").slider(
			{
				range: true,
				min: 0,
				max: 1000,
				values: [ 0, 580 ],
				slide: function( event, ui )
				{
					$( "#amount" ).val( "$" + ui.values[ 0 ] + " - $" + ui.values[ 1 ] );
				}
			});
				
			$( "#amount" ).val( "$" + $( "#slider-range" ).slider( "values", 0 ) + " - $" + $( "#slider-range" ).slider( "values", 1 ) );
			$('.ui-slider-handle').on('mouseup', function()
			{
				$('.product_grid').isotope({
		            filter: function()
		            {
		            	var priceRange = $('#amount').val();
			        	var priceMin = parseFloat(priceRange.split('-')[0].replace('$', ''));
			        	var priceMax = parseFloat(priceRange.split('-')[1].replace('$', ''));
			        	var itemPrice = $(this).find('.product_price').clone().children().remove().end().text().replace( '$', '' );

			        	return (itemPrice > priceMin) && (itemPrice < priceMax);
		            },
		            animationOptions: {
		                duration: 750,
		                easing: 'linear',
		                queue: false
		            }
		        });
			});
    	}	
    }

    /* 

	9. Init Favorites

	*/

	function initFavs()
	{
		// Handle Favorites
		var items = document.getElementsByClassName('product_fav');
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('click', function(fn)
			{
				fn.target.classList.toggle('active');
			});
		}
	}
});
/* JS Document */

/******************************

[Table of Contents]

1. Vars and Inits
2. Set Header
3. Init Menu
4. Init Thumbnail
5. Init Quantity
6. Init Star Rating
7. Init Favorite
8. Init Tabs



******************************/

jQuery(document).ready(function($)
{
	"use strict";

	/* 

	1. Vars and Inits

	*/

	var header = $('.header');
	var topNav = $('.top_nav')
	var hamburger = $('.hamburger_container');
	var menu = $('.hamburger_menu');
	var menuActive = false;
	var hamburgerClose = $('.hamburger_close');
	var fsOverlay = $('.fs_menu_overlay');

	setHeader();

	$(window).on('resize', function()
	{
		setHeader();
	});

	$(document).on('scroll', function()
	{
		setHeader();
	});

	initMenu();
	initThumbnail();
	initQuantity();
	initStarRating();
	initFavorite();
	initTabs();

	/* 

	2. Set Header

	*/

	function setHeader()
	{
		if(window.innerWidth < 992)
		{
			if($(window).scrollTop() > 100)
			{
				header.css({'top':"0"});
			}
			else
			{
				header.css({'top':"0"});
			}
		}
		else
		{
			if($(window).scrollTop() > 100)
			{
				header.css({'top':"-50px"});
			}
			else
			{
				header.css({'top':"0"});
			}
		}
		if(window.innerWidth > 991 && menuActive)
		{
			closeMenu();
		}
	}

	/* 

	3. Init Menu

	*/

	function initMenu()
	{
		if(hamburger.length)
		{
			hamburger.on('click', function()
			{
				if(!menuActive)
				{
					openMenu();
				}
			});
		}

		if(fsOverlay.length)
		{
			fsOverlay.on('click', function()
			{
				if(menuActive)
				{
					closeMenu();
				}
			});
		}

		if(hamburgerClose.length)
		{
			hamburgerClose.on('click', function()
			{
				if(menuActive)
				{
					closeMenu();
				}
			});
		}

		if($('.menu_item').length)
		{
			var items = document.getElementsByClassName('menu_item');
			var i;

			for(i = 0; i < items.length; i++)
			{
				if(items[i].classList.contains("has-children"))
				{
					items[i].onclick = function()
					{
						this.classList.toggle("active");
						var panel = this.children[1];
					    if(panel.style.maxHeight)
					    {
					    	panel.style.maxHeight = null;
					    }
					    else
					    {
					    	panel.style.maxHeight = panel.scrollHeight + "px";
					    }
					}
				}	
			}
		}
	}

	function openMenu()
	{
		menu.addClass('active');
		// menu.css('right', "0");
		fsOverlay.css('pointer-events', "auto");
		menuActive = true;
	}

	function closeMenu()
	{
		menu.removeClass('active');
		fsOverlay.css('pointer-events', "none");
		menuActive = false;
	}

	/* 

	4. Init Thumbnail

	*/

	function initThumbnail()
	{
		if($('.single_product_thumbnails ul li').length)
		{
			var thumbs = $('.single_product_thumbnails ul li');
			var singleImage = $('.single_product_image_background');

			thumbs.each(function()
			{
				var item = $(this);
				item.on('click', function()
				{
					thumbs.removeClass('active');
					item.addClass('active');
					var img = item.find('img').data('image');
					singleImage.css('background-image', 'url(' + img + ')');
				});
			});
		}	
	}

	/* 

	5. Init Quantity

	*/

	function initQuantity()
	{
		if($('.plus').length && $('.minus').length)
		{
			var plus = $('.plus');
			var minus = $('.minus');
			var value = $('#quantity_value');

			plus.on('click', function()
			{
				var x = parseInt(value.text());
				value.text(x + 1);
			});

			minus.on('click', function()
			{
				var x = parseInt(value.text());
				if(x > 1)
				{
					value.text(x - 1);
				}
			});
		}
	}

	/* 

	6. Init Star Rating

	*/

	function initStarRating()
	{
		if($('.user_star_rating li').length)
		{
			var stars = $('.user_star_rating li');

			stars.each(function()
			{
				var star = $(this);

				star.on('click', function()
				{
					var i = star.index();

					stars.find('i').each(function()
					{
						$(this).removeClass('fa-star');
						$(this).addClass('fa-star-o');
					});
					for(var x = 0; x <= i; x++)
					{
						$(stars[x]).find('i').removeClass('fa-star-o');
						$(stars[x]).find('i').addClass('fa-star');
					};
				});
			});
		}
	}

	/* 

	7. Init Favorite

	*/

	function initFavorite()
	{
		if($('.product_favorite').length)
		{
			var fav = $('.product_favorite');

			fav.on('click', function()
			{
				fav.toggleClass('active');
			});
		}
	}

	/* 

	8. Init Tabs

	*/

	function initTabs()
	{
		if($('.tabs').length)
		{
			var tabs = $('.tabs li');
			var tabContainers = $('.tab_container');

			tabs.each(function()
			{
				var tab = $(this);
				var tab_id = tab.data('active-tab');

				tab.on('click', function()
				{
					if(!tab.hasClass('active'))
					{
						tabs.removeClass('active');
						tabContainers.removeClass('active');
						tab.addClass('active');
						$('#' + tab_id).addClass('active');
					}
				});
			});
		}
	}
});
/* JS Document */

/******************************

[Table of Contents]

1. Vars and Inits
2. Set Header
3. Init Custom Dropdown
4. Init Page Menu
5. Init Deals Slider
6. Init Tab Lines
7. Init Tabs
8. Init Featured Slider
9. Init Favorites
10. Init ZIndex
11. Init Popular Categories Slider
12. Init Banner 2 Slider
13. Init Arrivals Slider
14. Init Arrivals Slider ZIndex
15. Init Best Sellers Slider
16. Init Trends Slider



******************************/

$(document).ready(function()
{
	"use strict";

	/* 

	1. Vars and Inits

	*/

	var menuActive = false;
	var header = $('.header');

	setHeader();

	initCustomDropdown();
	initPageMenu();
	initDealsSlider();
	initTabLines();
	initFeaturedSlider();
	featuredSliderZIndex();
	initPopularSlider();
	initBanner2Slider();
	initFavs();
	initArrivalsSlider();
	arrivalsSliderZIndex();
	bestsellersSlider();
	initTabs();
	initTrendsSlider();
	;

	$(window).on('resize', function()
	{
		setHeader();
		featuredSliderZIndex();
		initTabLines();
	});

	/* 

	2. Set Header

	*/

	function setHeader()
	{
		//To pin main nav to the top of the page when it's reached
		//uncomment the following

		// var controller = new ScrollMagic.Controller(
		// {
		// 	globalSceneOptions:
		// 	{
		// 		triggerHook: 'onLeave'
		// 	}
		// });

		// var pin = new ScrollMagic.Scene(
		// {
		// 	triggerElement: '.main_nav'
		// })
		// .setPin('.main_nav').addTo(controller);

		if(window.innerWidth > 991 && menuActive)
		{
			closeMenu();
		}
	}

	/* 

	3. Init Custom Dropdown

	*/

	function initCustomDropdown()
	{
		if($('.custom_dropdown_placeholder').length && $('.custom_list').length)
		{
			var placeholder = $('.custom_dropdown_placeholder');
			var list = $('.custom_list');
		}

		placeholder.on('click', function (ev)
		{
			if(list.hasClass('active'))
			{
				list.removeClass('active');
			}
			else
			{
				list.addClass('active');
			}

			$(document).one('click', function closeForm(e)
			{
				if($(e.target).hasClass('clc'))
				{
					$(document).one('click', closeForm);
				}
				else
				{
					list.removeClass('active');
				}
			});

		});

		$('.custom_list a').on('click', function (ev)
		{
			ev.preventDefault();
			var index = $(this).parent().index();

			placeholder.text( $(this).text() ).css('opacity', '1');

			if(list.hasClass('active'))
			{
				list.removeClass('active');
			}
			else
			{
				list.addClass('active');
			}
		});


		$('select').on('change', function (e)
		{
			placeholder.text(this.value);

			$(this).animate({width: placeholder.width() + 'px' });
		});
	}

	/* 

	4. Init Page Menu

	*/
	function initPageMenu()
	{
		if($('.page_menu').length && $('.page_menu_content').length)
		{
			var menu = $('.page_menu');
			var menuContent = $('.page_menu_content');
			var menuTrigger = $('.menu_trigger');

			//Open / close page menu
			menuTrigger.on('click', function()
			{
				if(!menuActive)
				{
					openMenu();
				}
				else
				{
					closeMenu();
				}
			});

			//Handle page menu
			if($('.page_menu_item').length)
			{
				var items = $('.page_menu_item');
				items.each(function()
				{
					var item = $(this);
					if(item.hasClass("has-children"))
					{
						item.on('click', function(evt)
						{
							evt.preventDefault();
							evt.stopPropagation();
							var subItem = item.find('> ul');
						    if(subItem.hasClass('active'))
						    {
						    	subItem.toggleClass('active');
								TweenMax.to(subItem, 0.3, {height:0});
						    }
						    else
						    {
						    	subItem.toggleClass('active');
						    	TweenMax.set(subItem, {height:"auto"});
								TweenMax.from(subItem, 0.3, {height:0});
						    }
						});
					}
				});
			}
		}
	}

	function openMenu()
	{
		var menu = $('.page_menu');
		var menuContent = $('.page_menu_content');
		TweenMax.set(menuContent, {height:"auto"});
		TweenMax.from(menuContent, 0.3, {height:0});
		menuActive = true;
	}

	function closeMenu()
	{
		var menu = $('.page_menu');
		var menuContent = $('.page_menu_content');
		TweenMax.to(menuContent, 0.3, {height:0});
		menuActive = false;
	}

	/* 

	5. Init Deals Slider

	*/

	function initDealsSlider()
	{
		if($('.deals_slider').length)
		{
			var dealsSlider = $('.deals_slider');
			dealsSlider.owlCarousel(
			{
				items:1,
				loop:false,
				navClass:['deals_slider_prev', 'deals_slider_next'],
				nav:false,
				dots:false,
				smartSpeed:1200,
				margin:30,
				autoplay:false,
				autoplayTimeout:5000
			});

			if($('.deals_slider_prev').length)
			{
				var prev = $('.deals_slider_prev');
				prev.on('click', function()
				{
					dealsSlider.trigger('prev.owl.carousel');
				});	
			}

			if($('.deals_slider_next').length)
			{
				var next = $('.deals_slider_next');
				next.on('click', function()
				{
					dealsSlider.trigger('next.owl.carousel');
				});	
			}
		}
	}

	/* 

	6. Init Tab Lines

	*/

	function initTabLines()
	{
		if($('.tabs').length)
		{
			var tabs = $('.tabs');

			tabs.each(function()
			{
				var tabsItem = $(this);
				var tabsLine = tabsItem.find('.tabs_line span');
				var tabGroup = tabsItem.find('ul li');

				var posX = $(tabGroup[0]).position().left;
				tabsLine.css({'left': posX, 'width': $(tabGroup[0]).width()});
				tabGroup.each(function()
				{
					var tab = $(this);
					tab.on('click', function()
					{
						if(!tab.hasClass('active'))
						{
							tabGroup.removeClass('active');
							tab.toggleClass('active');
							var tabXPos = tab.position().left;
							var tabWidth = tab.width();
							tabsLine.css({'left': tabXPos, 'width': tabWidth});
						}
					});
				});
			});
		}
	}

	/* 

	7. Init Tabs

	*/

	function initTabs()
	{
		if($('.tabbed_container').length)
		{
			//Handle tabs switching

			var tabsContainers = $('.tabbed_container');
			tabsContainers.each(function()
			{
				var tabContainer = $(this);
				var tabs = tabContainer.find('.tabs ul li');
				var panels = tabContainer.find('.panel');
				var sliders = panels.find('.slider');

				tabs.each(function()
				{
					var tab = $(this);
					tab.on('click', function()
					{
						panels.removeClass('active');
						var tabIndex = tabs.index(this);
						$($(panels[tabIndex]).addClass('active'));
						sliders.slick("unslick");
						sliders.each(function()
						{
							var slider = $(this);
							// slider.slick("unslick");
							if(slider.hasClass('bestsellers_slider'))
							{
								initBSSlider(slider);
							}
							if(slider.hasClass('featured_slider'))
							{
								initFSlider(slider);
							}
							if(slider.hasClass('arrivals_slider'))
							{
								initASlider(slider);
							}
						});
					});	
				});
			});
		}
	}

	/* 

	8. Init Featured Slider

	*/

	function initFeaturedSlider()
	{
		if($('.featured_slider').length)
		{
			var featuredSliders = $('.featured_slider');
			featuredSliders.each(function()
			{
				var featuredSlider = $(this);
				initFSlider(featuredSlider);
			});
				
		}
	}

	function initFSlider(fs)
	{
		var featuredSlider = fs;
		featuredSlider.on('init', function()
		{
			var activeItems = featuredSlider.find('.slick-slide.slick-active');
			for(var x = 0; x < activeItems.length - 1; x++)
			{
				var item = $(activeItems[x]);
				item.find('.border_active').removeClass('active');
				if(item.hasClass('slick-active'))
				{
					item.find('.border_active').addClass('active');
				}
			}
		}).on(
		{
			afterChange: function(event, slick, current_slide_index, next_slide_index)
			{
				var activeItems = featuredSlider.find('.slick-slide.slick-active');
				activeItems.find('.border_active').removeClass('active');
				for(var x = 0; x < activeItems.length - 1; x++)
				{
					var item = $(activeItems[x]);
					item.find('.border_active').removeClass('active');
					if(item.hasClass('slick-active'))
					{
						item.find('.border_active').addClass('active');
					}
				}
			}
		})
		.slick(
		{
			rows:2,
			slidesToShow:4,
			slidesToScroll:4,
			infinite:false,
			arrows:false,
			dots:true,
			responsive:
			[
				{
					breakpoint:768, settings:
					{
						rows:2,
						slidesToShow:3,
						slidesToScroll:3,
						dots:true
					}
				},
				{
					breakpoint:575, settings:
					{
						rows:2,
						slidesToShow:2,
						slidesToScroll:2,
						dots:false
					}
				},
				{
					breakpoint:480, settings:
					{
						rows:1,
						slidesToShow:1,
						slidesToScroll:1,
						dots:false
					}
				}
			]
		});
	}

	/* 

	9. Init Favorites

	*/

	function initFavs()
	{
		// Handle Favorites
		var items = document.getElementsByClassName('product_fav');
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('click', function(fn)
			{
				fn.target.classList.toggle('active');
			});
		}
	}

	/* 

	10. Init ZIndex

	*/

	function featuredSliderZIndex()
	{
		// Hide slider dots on item hover
		var items = document.getElementsByClassName('featured_slider_item');
		
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('mouseenter', function()
			{
				$('.featured_slider .slick-dots').css('display', "none");
			});

			item.addEventListener('mouseleave', function()
			{
				$('.featured_slider .slick-dots').css('display', "block");
			});
		}
	}
		/* 

	11. Init Popular Categories Slider

	*/

	function initPopularSlider()
	{
		if($('.popular_categories_slider').length)
		{
			var popularSlider = $('.popular_categories_slider');

			popularSlider.owlCarousel(
			{
				loop:true,
				autoplay:false,
				nav:false,
				dots:false,
				responsive:
				{
					0:{items:1},
					575:{items:2},
					640:{items:3},
					768:{items:4},
					991:{items:5}
				}
			});

			if($('.popular_categories_prev').length)
			{
				var prev = $('.popular_categories_prev');
				prev.on('click', function()
				{
					popularSlider.trigger('prev.owl.carousel');
				});
			}

			if($('.popular_categories_next').length)
			{
				var next = $('.popular_categories_next');
				next.on('click', function()
				{
					popularSlider.trigger('next.owl.carousel');
				});
			}
		}
	}

	/* 

	12. Init Banner 2 Slider

	*/

	function initBanner2Slider()
	{
		if($('.banner_2_slider').length)
		{
			var banner2Slider = $('.banner_2_slider');
			banner2Slider.owlCarousel(
			{
				items:1,
				loop:true,
				nav:false,
				dots:true,
				dotsContainer: '.banner_2_dots',
				smartSpeed:1200
			});
		}
	}

	/* 

	13. Init Arrivals Slider

	*/

	function initArrivalsSlider()
	{
		if($('.arrivals_slider').length)
		{
			var arrivalsSliders = $('.arrivals_slider');
			arrivalsSliders.each(function()
			{
				var arrivalsSlider = $(this);
				initASlider(arrivalsSlider);
			});	
			
		}
	}

	function initASlider(as)
	{
		var arrivalsSlider = as;
		arrivalsSlider.on('init', function()
		{
			var activeItems = arrivalsSlider.find('.slick-slide.slick-active');
			for(var x = 0; x < activeItems.length - 1; x++)
			{
				var item = $(activeItems[x]);
				item.find('.border_active').removeClass('active');
				if(item.hasClass('slick-active'))
				{
					item.find('.border_active').addClass('active');
				}
			}
		}).on(
		{
			afterChange: function(event, slick, current_slide_index, next_slide_index)
			{
				var activeItems = arrivalsSlider.find('.slick-slide.slick-active');
				activeItems.find('.border_active').removeClass('active');
				for(var x = 0; x < activeItems.length - 1; x++)
				{
					var item = $(activeItems[x]);
					item.find('.border_active').removeClass('active');
					if(item.hasClass('slick-active'))
					{
						item.find('.border_active').addClass('active');
					}
				}
			}
		})
		.slick(
		{
			rows:2,
			slidesToShow:5,
			slidesToScroll:5,
			infinite:false,
			arrows:false,
			dots:true,
			responsive:
			[
				{
					breakpoint:768, settings:
					{
						rows:2,
						slidesToShow:3,
						slidesToScroll:3,
						dots:true
					}
				},
				{
					breakpoint:575, settings:
					{
						rows:2,
						slidesToShow:2,
						slidesToScroll:2,
						dots:false
					}
				},
				{
					breakpoint:480, settings:
					{
						rows:1,
						slidesToShow:1,
						slidesToScroll:1,
						dots:false
					}
				}
			]
		});
	}

	/* 

	14. Init Arrivals Slider ZIndex

	*/

	function arrivalsSliderZIndex()
	{
		// Hide slider dots on item hover
		var items = document.getElementsByClassName('arrivals_slider_item');
		
		for(var x = 0; x < items.length; x++)
		{
			var item = items[x];
			item.addEventListener('mouseenter', function()
			{
				$('.arrivals_slider .slick-dots').css('display', "none");
			});

			item.addEventListener('mouseleave', function()
			{
				$('.arrivals_slider .slick-dots').css('display', "block");
			});
		}
	}

	/* 

	15. Init Best Sellers Slider

	*/

	function bestsellersSlider()
	{
		if($('.bestsellers_slider').length)
		{
			var bestsellersSliders = $('.bestsellers_slider');
			bestsellersSliders.each(function()
			{
				var bestsellersSlider = $(this);

				initBSSlider(bestsellersSlider);
			})	
		}
	}

	function initBSSlider(bss)
	{
		var bestsellersSlider = bss;

		bestsellersSlider.slick(
		{
			rows:2,
			infinite:true,
			slidesToShow:3,
			slidesToScroll:3,
			arrows:false,
			dots:true,
			autoplay: true,
  			autoplaySpeed: 6000,
			responsive:
			[
				{
					breakpoint:1199, settings:
					{
						rows:2,
						slidesToShow:2,
						slidesToScroll:2,
						dots:true
					}
				},
				{
					breakpoint:991, settings:
					{
						rows:2,
						slidesToShow:1,
						slidesToScroll:1,
						dots:true
					}
				},
				{
					breakpoint:575, settings:
					{
						rows:1,
						slidesToShow:1,
						slidesToScroll:1,
						dots:false
					}
				}
			]
		});
	}

	/* 

	16. Init Trends Slider

	*/

	function initTrendsSlider()
	{
		if($('.trends_slider').length)
		{
			var trendsSlider = $('.trends_slider');
			trendsSlider.owlCarousel(
			{
				loop:false,
				margin:30,
				nav:false,
				dots:false,
				autoplayHoverPause:true,
				autoplay:false,
				responsive:
				{
					0:{items:1},
					575:{items:2},
					991:{items:3}
				}
			});

			trendsSlider.on('click', '.trends_fav', function (ev)
			{
			    $(ev.target).toggleClass('active');
			});

			if($('.trends_prev').length)
			{
				var prev = $('.trends_prev');
				prev.on('click', function()
				{
					trendsSlider.trigger('prev.owl.carousel');
				});
			}

			if($('.trends_next').length)
			{
				var next = $('.trends_next');
				next.on('click', function()
				{
					trendsSlider.trigger('next.owl.carousel');
				});
			}
		}
	}
});
