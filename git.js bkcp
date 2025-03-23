// dl btn . dont fuck my js

function showPopupForDevice(id, encodedSuffix) {
            if (!encodedSuffix) return;
            let suffix = atob(encodedSuffix); // Decode the encoded suffix
            const link = isMobileDevice() 
                ? `tg://resolve?domain=file2link_BDbot&start=${suffix}` 
                : `https://t.me/file2link_BDbot?start=${suffix}`;
            showPopup(link, "5", "false", id);
        }

        function isMobileDevice() {
            return /Mobi|Android|iPhone/i.test(navigator.userAgent);
        }

        function showPopup(link, time, newtab, id) {
            var popupOverlay = document.getElementById('popupOverlay');
            var popupClose = document.getElementById('popupClose');
            var popupOk = document.getElementById('popupOk');
            var popupCancel = document.getElementById('popupCancel');

            popupOverlay.style.display = 'flex';

            popupClose.onclick = function() {
                popupOverlay.style.display = 'none';
            };

            popupCancel.onclick = function() {
                popupOverlay.style.display = 'none';
            };

            popupOk.onclick = function() {
                popupOverlay.style.display = 'none';
                startDownload(link, time, newtab, id);
            };
        }

        function startDownload(link, time, newtab, id) {
            var dldCo = document.querySelector(id),
                dldMe = document.querySelector(id + ' .dldMe'),
                dldPg = document.querySelector(id + ' .dldPg'),
                dldDl = document.querySelector(id + ' .dldDl'),
                dldRt = document.querySelector(id + ' .dldRt'),
                dldLf = time;

            dldMe.innerHTML = 'Starting Download in <span>' + dldLf + '</span> seconds...';
            dldCo.classList.add('dldAlt');

            var downloadTimer = setInterval(function timeCount() {
                dldLf -= 1;
                dldMe.innerHTML = 'Starting Download in <span>' + dldLf + '</span> seconds...';
                dldPg.style.strokeDashoffset = Math.floor((dldLf / time) * 100);

                if (dldLf <= 0) {
                    clearInterval(downloadTimer);
                    dldMe.innerHTML = 'Please wait...';

                    if (newtab === 'true') {
                        window.open(link, '_blank');
                    } else {
                        window.location.href = link;
                    }

                    dldCo.classList.add('dldRty');
                    dldRt.onclick = function() {
                        if (newtab === 'true') {
                            window.open(link, '_blank');
                        } else {
                            window.location.href = link;
                        }
                    };
                }
            }, 1000);
        }
        
        
        




//screnshtot js . don fuck my js

document.addEventListener("DOMContentLoaded", function () {
    const gallery = document.querySelector(".screenshot-gallery");
    const images = document.querySelectorAll(".screenshot-gallery img");
    const popup = document.getElementById("screenshotPopup");
    const popupImage = document.getElementById("popupImage");
    const closeBtn = document.querySelector(".close-btn");
    const prevArrow = document.querySelector(".prev-arrow");
    const nextArrow = document.querySelector(".next-arrow");

    let currentIndex = 0;

    // Mouse wheel scroll for gallery
    gallery.addEventListener("wheel", (e) => {
        e.preventDefault();
        gallery.scrollLeft += e.deltaY;
    });

    // Open popup and set current index
    images.forEach((img, index) => {
        img.addEventListener("click", () => {
            currentIndex = index;
            popupImage.src = img.src;
            popup.style.display = "flex";
            
            // Push new state to prevent back navigation issue
            history.pushState({ popupOpen: true }, "", "#popup");
        });
    });

    // Function to close popup
    function closePopup() {
        popup.style.display = "none";
        
        // Remove hash from URL without reloading the page
        if (history.state && history.state.popupOpen) {
            history.back();
        }
    }

    // Close popup on button click
    closeBtn.addEventListener("click", closePopup);

    // Close popup with ESC key
    document.addEventListener("keydown", (e) => {
        if (e.key === "Escape" && popup.style.display === "flex") {
            closePopup();
        }
    });

    // Close popup when clicking outside
    popup.addEventListener("click", (e) => {
        if (e.target === popup) {
            closePopup();
        }
    });

    // Previous image
    prevArrow.addEventListener("click", () => {
        if (currentIndex > 0) {
            currentIndex--;
            popupImage.src = images[currentIndex].src;
        }
    });

    // Next image
    nextArrow.addEventListener("click", () => {
        if (currentIndex < images.length - 1) {
            currentIndex++;
            popupImage.src = images[currentIndex].src;
        }
    });

    // Keyboard navigation (left and right arrows)
    document.addEventListener("keydown", (e) => {
        if (popup.style.display === "flex") {
            if (e.key === "ArrowLeft" && currentIndex > 0) {
                currentIndex--;
                popupImage.src = images[currentIndex].src;
            } else if (e.key === "ArrowRight" && currentIndex < images.length - 1) {
                currentIndex++;
                popupImage.src = images[currentIndex].src;
            }
        }
    });

    // Handle back button to close popup
    window.addEventListener("popstate", (e) => {
        if (popup.style.display === "flex") {
            closePopup();
        }
    });
});