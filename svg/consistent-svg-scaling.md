# Consistent SVG scaling (including IE)

Here's a quick way to get an SVG to scale down like an `<img>` in a responsive
layout. IE and some older browsers will auto-scale the image area to keep the
width:height aspect ratio constant, but it won't scale the actual drawing to
match the scale of the image dimensions.

HTML:

    <div class="svg__container">
        <svg class="svg" viewBox="0 0 60 55">
            <!-- SVG content -->
        </svg>
    </div>

CSS:

    .svg__container {
        position: relative;
        width: 100%;
        height: 0;

        /* 100% width, multiplied by the SVG height/width */
        padding-bottom: calc(100% * 55/60);
    }

    .svg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

If the `svg__container` also has a percentage width, use that in the padding-bottom
calculation:

    .svg__container {
        width: 65%;
        padding-bottom: calc(65% * 55/60);
    }

I also made a Sass mixin to make this easier:

    /**
     * Calculates the padding and width of an element so it maintains it's
     * aspect ratio.
     *
     * @int $width        Element width at 100%
     * @int $height       Element height at 100%
     * @int $container    Unitless width of the parent container
     *
     * @author Dave A
     */
    @mixin aspect-ratio($width, $height, $container: 364) {
        $output-width: floor(percentage($width/$container));
        width: $output-width;
        padding-bottom: calc(#{$output-width} * #{$height}/#{$width});
    }

[Source](https://css-tricks.com/scale-svg/)
