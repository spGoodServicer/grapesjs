# grapesjs
Create dropdown menu inside options panel
![image](https://user-images.githubusercontent.com/106048648/211146238-9ba75ad6-ca83-4479-b52f-2304a8ddd738.png)


var devicesDropdownDiv = document.createElement('div');
                                            devicesDropdownDiv.className='gjs-dropdown';
                                            devicesDropdownDiv.innerHTML = `
                                                <div class="select-device all">All Devices</div>
                                                <div class="options">
                                                    <div class="all" data-value="Laptop">All Devices</div>
                                                    <div class="laptop" data-value="Laptop">Laptop</div>
                                                    <div class="tablet" data-value="Tablet">Tablet</div>
                                                    <div class="mobile" data-value="Mobile">Mobile</div>
                                                </div>
                                            `;
                                            //let dropdown = document.querySelector(".gjs-dropdown");
                                            let selectDevice = devicesDropdownDiv.querySelector(".select-device");
                                            let options = devicesDropdownDiv.querySelector(".options");
                                            let optionItems = options.querySelectorAll("div");
                                            const toggleDropdown = () => {
                                                if (window.getComputedStyle(options).display == "none") {
                                                    options.style.display = "block";
                                                }
                                                else {
                                                    options.style.display = "none";
                                                }           
                                            }   
                                            selectDevice.addEventListener("click", toggleDropdown);
                                            
                                            
                                            const chooseOption = (option) => {
                                                e.setDevice(option.getAttribute("data-value"));
                                                selectDevice.innerHTML = option.innerHTML;
                                                selectDevice.className="select-device";
                                                selectDevice.classList.add(option.className);
                                                toggleDropdown();
                                            }
                                            optionItems.forEach(function(option, i) {
                                                option.addEventListener("click", function(){chooseOption(option)});
                                            });
                                            
                                            const closeDropdown = (e) => {
                                                if (e.target.parentNode.className !== "gjs-dropdown") {
                                                    options.style.display = "none";
                                                }
                                            }
                                            document.addEventListener("click", closeDropdown);
                                            e.Panels.getPanel('devices').set("appendContent",devicesDropdownDiv);
