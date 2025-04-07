---
layout: page
permalink: /awards/
title: Awards
description: Noteworthy honors and awards Md Abrar Jahin received in reversed chronological order.
nav: true
nav_order: 3
---


<div class="container">
    {% assign month_map = "January,1|February,2|March,3|April,4|May,5|June,6|July,7|August,8|September,9|October,10|November,11|December,12" | split: "|" %}
    
    {% assign awards = site.data.awards %}
    {% for award in awards %}
        {% assign month_number = 0 %}
        {% for map in month_map %}
            {% assign key_value = map | split: "," %}
            {% if award.month == key_value[0] %}
                {% assign month_number = key_value[1] %}
            {% endif %}
        {% endfor %}
        {% assign timestamp = award.year | append: "-" | append: month_number | append: "-01" | date: "%s" %}
        {% assign award.timestamp = timestamp %}
    {% endfor %}
    
    {% assign sorted_awards = awards | sort: "timestamp" %}

    {% for award in sorted_awards %}
    <div class="row mb-4">
        <div class="col-12 col-md-2 mb-2">
            <p class="text-muted">{{ award.year }} - {{ award.month }}</p>
            {% for image in award.preview_images %}
            <img data-zoomable class="preview z-depth-1 rounded" src="{{ image }}" alt="Award Preview" class="img-fluid mb-2">
            {% endfor %}
        </div>
        <div class="col-12 col-md-8">
            <h5>{{ award.title }}</h5>
            <p class="award-description">
                <span id="awardDescription{{ forloop.index }}" class="award-description truncated">{{ award.description | truncatewords: 30 }}</span>
                <span id="awardDescriptionFull{{ forloop.index }}" class="award-description-full" style="display: none;">{{ award.description }}</span>
                {% if award.description | size > 30 %}
                <button onclick="toggleDescription({{ forloop.index }})" id="toggleBtn{{ forloop.index }}" class="toggle-btn">Read more</button>
                {% endif %}
            </p>
            {% if award.certificate %}
                <p><a href="{{ award.certificate }}" target="_blank"><i class="fa-solid fa-award"></i> Certificate</a></p>
            {% endif %}
            {% if award.pdf %}
                <p><a href="{{ award.pdf }}" target="_blank"><i class="fa-solid fa-file-pdf"></i> PDF</a></p>
            {% endif %}
            {% if award.facebook %}
                <p><a href="{{ award.facebook }}" target="_blank"><i class="fab fa-facebook-square"></i> Facebook reference</a></p>
            {% endif %}
            {% if award.linkedin %}
                <p><a href="{{ award.linkedin }}" target="_blank"><i class="fa-brands fa-linkedin"></i> LinkedIn reference</a></p>
            {% endif %}
            {% if award.twitter %}
                <p><a href="{{ award.twitter }}" target="_blank"><i class="fab fa-twitter"></i> Twitter reference</a></p>
            {% endif %}
            {% if award.youtube %}
                <p><a href="{{ award.youtube }}" target="_blank"><i class="fab fa-youtube"></i> YouTube video</a></p>
            {% endif %}
            {% if award.external_link %}
                <p><a href="{{ award.external_link }}" target="_blank"><i class="fa-solid fa-up-right-from-square"></i> Link</a></p>
            {% endif %}
            {% if award.website %}
                <p><a href="{{ award.website }}" target="_blank"><i class="fa-solid fa-globe"></i> Website</a></p>
            {% endif %}
            {% if award.code %}
                <p><a href="{{ award.code }}" target="_blank"><i class="fa-brands fa-square-github"></i> Code</a></p>
            {% endif %}
            {% if award.embed_post %}
                <div class="mb-3">
                    {{ award.embed_post | safe }}
                </div>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>


<style>
    .award-description-full {
        display: none;
    }

    .toggle-btn {
        background-color: #007bff;
        color: white;
        border: none;
        padding: 5px 10px;
        cursor: pointer;
        border-radius: 5px;
    }
</style>

<script>
    function toggleDescription(index) {
        var description = document.getElementById('awardDescription' + index);
        var fullDescription = document.getElementById('awardDescriptionFull' + index);
        var btn = document.getElementById('toggleBtn' + index);

        if (description.style.display === "none") {
            description.style.display = "inline";
            fullDescription.style.display = "none";
            btn.innerHTML = "Read more"; 
        } else {
            description.style.display = "none";
            fullDescription.style.display = "inline";
            btn.innerHTML = "Read less"; 
        }
    }
</script>





