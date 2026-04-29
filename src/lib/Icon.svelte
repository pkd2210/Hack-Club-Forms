<script>

    import { onMount } from "svelte";
    import { on } from "svelte/events";
    let { glyph, size = 24, color = 'currentColor', class: className = '', style = '' } = $props();

    const url = $derived(`https://icons.hackclub.com/api/icons/${color}/${glyph}`);
    let svg = $state('');
    onMount(() => {
        fetchIcon();
    });

    function fetchIcon() {
        if (glyph) {
            svg = '';
            fetch(url)
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`Icon fetch error: ${response.status}`);
                    }
                    return response.text();
                })
                .then(data => {
                    // Add size and class to the SVG element
                    const parser = new DOMParser();
                    const doc = parser.parseFromString(data, 'image/svg+xml');
                    const svgElement = doc.querySelector('svg');
                    if (svgElement) {
                        svgElement.setAttribute('width', size);
                        svgElement.setAttribute('height', size);
                        if (className) {
                            svgElement.setAttribute('class', className);
                        }
                        let combinedStyle = style ? `${style}; display: inline-block;` : 'display: inline-block;';
                        svgElement.setAttribute('style', combinedStyle);
                        svg = new XMLSerializer().serializeToString(svgElement);
                    } else {
                        svg = '';
                    }
                })
                .catch(error => {
                    console.error('Icon fetch error:', error);
                    svg = '';
                });
        } else {
            svg = '';
        }
    }
</script>
{@html svg}