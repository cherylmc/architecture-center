---
title: Predicting Length of Stay in Hospitals
titleSuffix: Azure Solution Ideas
author: adamboeglin
ms.date: 12/16/2019
description: This solution enables a predictive model for Length of Stay for in-hospital admissions. Length of Stay (LOS) is defined in number of days from the initial admit date to the date that the patient is discharged from any given hospital facility.
ms.custom: acom-architecture, artificial intelligence, solution architectures, Azure, ai gallery, 'https://azure.microsoft.com/solutions/architecture/predicting-length-of-stay-in-hospitals/'
---
# Predicting Length of Stay in Hospitals

[!INCLUDE [header_file](../header.md)]

This solution enables a predictive model for Length of Stay for in-hospital admissions. Length of Stay (LOS) is defined in number of days from the initial admit date to the date that the patient is discharged from any given hospital facility.

## Architecture

<svg class="architecture-diagram" aria-labelledby="predicting-length-of-stay-in-hospitals" height="71.779" viewbox="0 0 811.074 71.779" width="811.074" xmlns="http://www.w3.org/2000/svg">
    <g data-name="Layer 2">
        <g data-name="Layer 1">
            <g fill="#969696">
                <path d="M124.921 22.731h238.266v1.5H124.921z"/>
                <path d="M361.655 18.246l9.067 5.235-9.067 5.236V18.246z"/>
            </g>
            <g fill="#969696">
                <path d="M459.921 22.731h239.266v1.5H459.921z"/>
                <path d="M697.655 18.246l9.067 5.235-9.067 5.236V18.246z"/>
            </g>
            <g fill="#5b5b5b">
                <path d="M382.074 67.9H380.8l-1.039-2.748h-4.156l-.975 2.748h-1.278l3.76-9.8h1.188zm-2.687-3.78l-1.538-4.177a3.9 3.9 0 01-.15-.656h-.027a3.647 3.647 0 01-.157.656l-1.524 4.177zM388.247 61.224l-4.147 5.722h4.1v.954h-5.749v-.349l4.149-5.691h-3.753v-.96h5.4zM395.356 67.9h-1.121v-1.1h-.027a2.3 2.3 0 01-2.16 1.271q-2.5 0-2.5-2.98V60.9h1.114v4.006q0 2.215 1.7 2.215a1.716 1.716 0 001.35-.6 2.317 2.317 0 00.53-1.583V60.9h1.121zM401.27 62.037a1.372 1.372 0 00-.848-.226 1.429 1.429 0 00-1.2.677 3.122 3.122 0 00-.482 1.846V67.9h-1.121v-7h1.121v1.442h.027a2.447 2.447 0 01.731-1.152 1.668 1.668 0 011.1-.413 1.841 1.841 0 01.67.1zM407.928 64.683h-4.942a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.683 1.484zM413.608 67.9v-9.8h2.707q5.181 0 5.182 4.778a4.814 4.814 0 01-1.438 3.646 5.338 5.338 0 01-3.853 1.378zm1.148-8.764v7.725h1.463a4.155 4.155 0 003-1.032 3.872 3.872 0 001.073-2.926q0-3.768-4.006-3.767zM422.967 67.506v-1.353a2.625 2.625 0 00.557.369 4.466 4.466 0 00.684.276 5.349 5.349 0 00.722.175 4.018 4.018 0 00.67.062 2.631 2.631 0 001.583-.393 1.333 1.333 0 00.522-1.132 1.317 1.317 0 00-.175-.69 1.961 1.961 0 00-.481-.537 4.9 4.9 0 00-.728-.465q-.422-.221-.906-.468-.513-.259-.957-.526a4.1 4.1 0 01-.772-.588 2.472 2.472 0 01-.517-.729 2.484 2.484 0 01.106-2.119 2.529 2.529 0 01.772-.816 3.5 3.5 0 011.09-.479 4.968 4.968 0 011.248-.157 4.783 4.783 0 012.112.349v1.292a3.826 3.826 0 00-2.229-.6 3.643 3.643 0 00-.752.079 2.093 2.093 0 00-.67.256 1.491 1.491 0 00-.479.458 1.216 1.216 0 00-.185.684 1.4 1.4 0 00.141.649 1.584 1.584 0 00.413.5 4.132 4.132 0 00.667.438q.393.212.905.465t1 .547a4.573 4.573 0 01.827.636 2.859 2.859 0 01.564.772 2.176 2.176 0 01.208.971 2.462 2.462 0 01-.284 1.228 2.315 2.315 0 01-.766.816 3.357 3.357 0 01-1.11.455 6.122 6.122 0 01-1.326.14 5.326 5.326 0 01-.574-.038q-.341-.037-.7-.109a5.325 5.325 0 01-.673-.178 2.048 2.048 0 01-.507-.24zM438.149 58.1l-3.63 9.8h-1.265l-3.554-9.8h1.278l2.714 7.772a4.6 4.6 0 01.2.868h.027a4.217 4.217 0 01.226-.882l2.769-7.759zM449.552 67.9h-1.142v-6.574q0-.779.1-1.907h-.027a6.085 6.085 0 01-.294.95l-3.35 7.533h-.561l-3.343-7.479a5.889 5.889 0 01-.294-1h-.027q.054.589.055 1.921V67.9h-1.107v-9.8h1.518l3.008 6.836a8.77 8.77 0 01.451 1.176h.041c.2-.538.353-.938.472-1.2l3.069-6.809h1.436z"/>
            </g>
            <g fill="#5b5b5b">
                <path d="M572.794 13.506v-1.353a2.633 2.633 0 00.558.369 4.349 4.349 0 00.684.276 5.231 5.231 0 00.721.175 4.018 4.018 0 00.67.062 2.624 2.624 0 001.582-.393 1.476 1.476 0 00.35-1.822 2 2 0 00-.482-.537 4.815 4.815 0 00-.729-.465c-.279-.147-.582-.3-.905-.468q-.513-.259-.957-.526a4.13 4.13 0 01-.772-.588 2.451 2.451 0 01-.514-.729 2.237 2.237 0 01-.188-.953 2.241 2.241 0 01.294-1.166 2.519 2.519 0 01.772-.816 3.5 3.5 0 011.091-.479 4.955 4.955 0 011.247-.157 4.783 4.783 0 012.112.349v1.291a3.829 3.829 0 00-2.229-.6 3.636 3.636 0 00-.752.079 2.084 2.084 0 00-.67.256 1.491 1.491 0 00-.479.458 1.216 1.216 0 00-.185.684 1.413 1.413 0 00.14.649 1.6 1.6 0 00.414.5 4.121 4.121 0 00.666.438q.394.212.906.465t1 .547a4.573 4.573 0 01.827.636 2.815 2.815 0 01.563.772 2.163 2.163 0 01.209.971 2.472 2.472 0 01-.283 1.228 2.341 2.341 0 01-.766.816 3.379 3.379 0 01-1.111.455 6.129 6.129 0 01-1.326.14 5.326 5.326 0 01-.574-.038q-.343-.037-.7-.109a5.43 5.43 0 01-.674-.178 2.09 2.09 0 01-.51-.239zM585.311 13.581a3.637 3.637 0 01-1.914.485 3.17 3.17 0 01-2.416-.974 3.533 3.533 0 01-.92-2.526 3.877 3.877 0 01.991-2.778 3.465 3.465 0 012.646-1.05 3.688 3.688 0 011.627.342v1.149a2.854 2.854 0 00-1.668-.547 2.254 2.254 0 00-1.76.769 2.917 2.917 0 00-.687 2.021 2.774 2.774 0 00.646 1.941 2.225 2.225 0 001.732.711 2.807 2.807 0 001.723-.608zM589.932 14.067a3.247 3.247 0 01-2.479-.981 3.632 3.632 0 01-.926-2.6 3.784 3.784 0 01.964-2.755 3.468 3.468 0 012.6-.991 3.138 3.138 0 012.443.964 3.82 3.82 0 01.879 2.673 3.757 3.757 0 01-.947 2.683 3.314 3.314 0 01-2.534 1.007zm.082-6.385a2.13 2.13 0 00-1.709.735 3.012 3.012 0 00-.629 2.026 2.855 2.855 0 00.636 1.962 2.161 2.161 0 001.7.718 2.054 2.054 0 001.672-.7 3.059 3.059 0 00.584-2 3.113 3.113 0 00-.584-2.023 2.044 2.044 0 00-1.67-.718zM598.859 8.037a1.372 1.372 0 00-.848-.226 1.429 1.429 0 00-1.2.677 3.122 3.122 0 00-.482 1.846V13.9h-1.121v-7h1.121v1.445h.027a2.447 2.447 0 01.731-1.152 1.668 1.668 0 011.1-.413 1.841 1.841 0 01.67.1zM605.518 10.683h-4.942a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.684 1.483z"/>
            </g>
            <g fill="#5b5b5b">
                <path d="M152.753 13.9V4.1h2.707q5.181 0 5.182 4.778a4.814 4.814 0 01-1.438 3.646 5.338 5.338 0 01-3.853 1.378zm1.147-8.761v7.725h1.463a4.155 4.155 0 003-1.032 3.872 3.872 0 001.073-2.926q0-3.768-4.006-3.767zM168.045 10.683H163.1a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.684 1.483zM175.243 6.9l-2.789 7h-1.1l-2.652-7h1.23l1.777 5.086a4.618 4.618 0 01.246.978h.027a4.545 4.545 0 01.219-.95l1.86-5.114zM181.99 10.683h-4.942a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.684 1.483zM184.807 13.9h-1.121V3.539h1.121zM190 14.067a3.247 3.247 0 01-2.479-.981 3.632 3.632 0 01-.926-2.6 3.784 3.784 0 01.964-2.755 3.468 3.468 0 012.6-.991 3.138 3.138 0 012.443.964 3.82 3.82 0 01.879 2.673 3.757 3.757 0 01-.947 2.683A3.314 3.314 0 01190 14.067zm.082-6.385a2.13 2.13 0 00-1.709.735 3.012 3.012 0 00-.629 2.026 2.855 2.855 0 00.636 1.962 2.161 2.161 0 001.7.718 2.054 2.054 0 001.672-.7 3.059 3.059 0 00.584-2 3.113 3.113 0 00-.584-2.023 2.044 2.044 0 00-1.668-.718zM196.428 12.891h-.028v4.231h-1.121V6.9h1.121v1.23h.027a2.65 2.65 0 012.42-1.395 2.563 2.563 0 012.112.94 3.89 3.89 0 01.759 2.519 4.344 4.344 0 01-.854 2.813 2.847 2.847 0 01-2.338 1.056 2.341 2.341 0 01-2.098-1.172zm-.027-2.823v.978a2.08 2.08 0 00.564 1.474 2.011 2.011 0 003.027-.175 3.569 3.569 0 00.578-2.167 2.819 2.819 0 00-.54-1.832 1.789 1.789 0 00-1.463-.663 1.985 1.985 0 00-1.567.68 2.5 2.5 0 00-.6 1.705zM212.355 13.9h-1.121v-1.091h-.027a2.347 2.347 0 01-2.153 1.258 2.3 2.3 0 01-1.638-.554 1.921 1.921 0 01-.591-1.47q0-1.961 2.311-2.283l2.1-.294q0-1.784-1.442-1.784a3.446 3.446 0 00-2.283.861V7.395a4.34 4.34 0 012.379-.656q2.468 0 2.468 2.611zm-1.121-3.541l-1.688.232a2.761 2.761 0 00-1.176.386 1.115 1.115 0 00-.4.981 1.066 1.066 0 00.366.837 1.41 1.41 0 00.974.325 1.8 1.8 0 001.378-.585 2.09 2.09 0 00.543-1.479zM220.278 13.9h-1.121V9.91q0-2.228-1.627-2.229a1.768 1.768 0 00-1.392.632 2.348 2.348 0 00-.55 1.6V13.9h-1.121v-7h1.121v1.165h.027a2.526 2.526 0 012.3-1.326 2.143 2.143 0 011.757.741 3.308 3.308 0 01.608 2.144zM228.365 13.9h-1.121v-1.187h-.027a2.589 2.589 0 01-2.406 1.354 2.616 2.616 0 01-2.109-.94 3.859 3.859 0 01-.789-2.56 4.192 4.192 0 01.875-2.782 2.885 2.885 0 012.331-1.046 2.243 2.243 0 012.1 1.135h.027V3.539h1.121zm-1.121-3.165v-1.03a2 2 0 00-.561-1.436 1.882 1.882 0 00-1.422-.588 1.936 1.936 0 00-1.613.752 3.291 3.291 0 00-.588 2.078 2.961 2.961 0 00.564 1.911 1.841 1.841 0 001.514.7 1.918 1.918 0 001.521-.677 2.527 2.527 0 00.585-1.707zM234.62 13.9V4.1h2.707q5.181 0 5.182 4.778a4.814 4.814 0 01-1.438 3.646 5.338 5.338 0 01-3.853 1.378zm1.148-8.764v7.725h1.463a4.155 4.155 0 003-1.032 3.872 3.872 0 001.073-2.926q0-3.768-4.006-3.767zM249.912 10.683h-4.942a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.684 1.483zM252.756 12.891h-.027v4.231h-1.121V6.9h1.121v1.23h.027a2.65 2.65 0 012.42-1.395 2.563 2.563 0 012.112.94 3.89 3.89 0 01.759 2.519 4.344 4.344 0 01-.854 2.813 2.847 2.847 0 01-2.338 1.056 2.341 2.341 0 01-2.099-1.172zm-.027-2.823v.978a2.08 2.08 0 00.564 1.474 2.011 2.011 0 003.027-.175 3.569 3.569 0 00.578-2.167 2.819 2.819 0 00-.54-1.832 1.789 1.789 0 00-1.463-.663 1.985 1.985 0 00-1.572.681 2.5 2.5 0 00-.594 1.704zM260.959 13.9h-1.121V3.539h1.121zM266.154 14.067a3.247 3.247 0 01-2.479-.981 3.632 3.632 0 01-.926-2.6 3.784 3.784 0 01.964-2.755 3.468 3.468 0 012.6-.991 3.138 3.138 0 012.443.964 3.82 3.82 0 01.879 2.673 3.757 3.757 0 01-.947 2.683 3.314 3.314 0 01-2.534 1.007zm.082-6.385a2.13 2.13 0 00-1.709.735 3.012 3.012 0 00-.629 2.026 2.855 2.855 0 00.636 1.962 2.161 2.161 0 001.7.718 2.054 2.054 0 001.672-.7 3.059 3.059 0 00.584-2 3.113 3.113 0 00-.584-2.023 2.044 2.044 0 00-1.67-.718zM277 6.9l-3.22 8.121q-.861 2.174-2.42 2.174a2.589 2.589 0 01-.731-.089v-1a2.073 2.073 0 00.663.123 1.375 1.375 0 001.271-1.012l.561-1.326-2.731-6.991h1.244l1.894 5.387q.034.1.144.533h.041q.034-.164.137-.52l1.989-5.4zM292.186 13.9h-1.142V7.326q0-.779.1-1.907h-.027a6.194 6.194 0 01-.294.95l-3.35 7.533h-.561l-3.343-7.479a5.8 5.8 0 01-.294-1h-.027q.054.589.055 1.921V13.9h-1.107V4.1h1.518l3.008 6.836a8.77 8.77 0 01.451 1.176h.041c.2-.538.354-.938.472-1.2L290.75 4.1h1.436zM297.538 14.067a3.245 3.245 0 01-2.478-.981 3.629 3.629 0 01-.927-2.6 3.784 3.784 0 01.967-2.756 3.468 3.468 0 012.6-.991 3.141 3.141 0 012.444.964 3.824 3.824 0 01.878 2.673 3.761 3.761 0 01-.946 2.683 3.318 3.318 0 01-2.538 1.008zm.082-6.385a2.132 2.132 0 00-1.709.735 3.017 3.017 0 00-.629 2.026 2.855 2.855 0 00.636 1.962 2.161 2.161 0 001.7.718 2.049 2.049 0 001.671-.7 3.048 3.048 0 00.585-2 3.1 3.1 0 00-.585-2.023 2.039 2.039 0 00-1.669-.718zM308.79 13.9h-1.121v-1.187h-.027a2.824 2.824 0 01-4.515.413 3.848 3.848 0 01-.79-2.56 4.2 4.2 0 01.875-2.782 2.885 2.885 0 012.331-1.046 2.244 2.244 0 012.1 1.135h.027V3.539h1.121zm-1.121-3.165v-1.03a2 2 0 00-.561-1.436 1.882 1.882 0 00-1.422-.588 1.936 1.936 0 00-1.613.752 3.3 3.3 0 00-.588 2.078 2.972 2.972 0 00.563 1.911 1.846 1.846 0 001.515.7 1.913 1.913 0 001.521-.677 2.518 2.518 0 00.585-1.707zM316.686 10.683h-4.942a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.684 1.483zM319.5 13.9h-1.121V3.539h1.121zM321.348 13.65v-1.2a3.318 3.318 0 002.017.677q1.477 0 1.477-.984a.861.861 0 00-.126-.476 1.3 1.3 0 00-.342-.345 2.671 2.671 0 00-.506-.271 34.39 34.39 0 00-.626-.249 8.246 8.246 0 01-.817-.372 2.541 2.541 0 01-.588-.424 1.6 1.6 0 01-.355-.537 1.916 1.916 0 01-.119-.7 1.677 1.677 0 01.226-.872 1.994 1.994 0 01.6-.635 2.764 2.764 0 01.858-.387 3.824 3.824 0 01.994-.13 4.013 4.013 0 011.627.314v1.129a3.175 3.175 0 00-1.777-.506 2.117 2.117 0 00-.567.071 1.407 1.407 0 00-.435.2.93.93 0 00-.279.312.813.813 0 00-.1.4.954.954 0 00.1.458 1 1 0 00.29.328 2.25 2.25 0 00.465.26q.274.117.622.253a8.453 8.453 0 01.834.366 2.831 2.831 0 01.629.424 1.655 1.655 0 01.4.543 1.764 1.764 0 01.14.731 1.717 1.717 0 01-.229.9 1.958 1.958 0 01-.611.636 2.821 2.821 0 01-.882.376 4.358 4.358 0 01-1.046.123 3.977 3.977 0 01-1.874-.413z"/>
            </g>
            <g fill="#5b5b5b">
                <path d="M710.251 58.1l-3.63 9.8h-1.265l-3.556-9.8h1.278l2.714 7.772a4.6 4.6 0 01.2.868h.027a4.217 4.217 0 01.226-.882l2.769-7.759zM712.083 59.125a.71.71 0 01-.513-.205.69.69 0 01-.212-.52.719.719 0 01.725-.731.719.719 0 01.522.209.728.728 0 010 1.035.718.718 0 01-.522.212zm.547 8.777h-1.121v-7h1.121zM714.476 67.65v-1.2a3.316 3.316 0 002.017.677q1.477 0 1.477-.984a.854.854 0 00-.127-.476 1.258 1.258 0 00-.342-.345 2.584 2.584 0 00-.506-.271c-.193-.079-.4-.162-.625-.249a8.022 8.022 0 01-.816-.372 2.48 2.48 0 01-.588-.424 1.559 1.559 0 01-.355-.537 1.9 1.9 0 01-.12-.7 1.677 1.677 0 01.226-.872 1.994 1.994 0 01.6-.635 2.768 2.768 0 01.857-.387 3.842 3.842 0 011-.13 4.01 4.01 0 011.627.314v1.135a3.173 3.173 0 00-1.777-.506 2.112 2.112 0 00-.567.071 1.391 1.391 0 00-.434.2.936.936 0 00-.281.312.823.823 0 00-.1.4.966.966 0 00.1.458 1.01 1.01 0 00.291.328 2.225 2.225 0 00.465.26c.182.078.39.162.622.253a8.453 8.453 0 01.834.366 2.808 2.808 0 01.629.424 1.638 1.638 0 01.4.543 1.749 1.749 0 01.141.731 1.726 1.726 0 01-.229.9 1.971 1.971 0 01-.612.636 2.821 2.821 0 01-.882.376 4.358 4.358 0 01-1.046.123 3.979 3.979 0 01-1.879-.419zM726.5 67.9h-1.121v-1.1h-.027a2.3 2.3 0 01-2.16 1.271q-2.5 0-2.5-2.98V60.9h1.108v4.006q0 2.215 1.7 2.215a1.719 1.719 0 001.351-.6 2.321 2.321 0 00.529-1.583V60.9h1.12zM733.773 67.9h-1.121v-1.091h-.027a2.347 2.347 0 01-2.153 1.258 2.3 2.3 0 01-1.638-.554 1.921 1.921 0 01-.591-1.47q0-1.961 2.311-2.283l2.1-.294q0-1.784-1.442-1.784a3.446 3.446 0 00-2.283.861v-1.148a4.34 4.34 0 012.379-.656q2.468 0 2.468 2.611zm-1.121-3.541l-1.688.232a2.761 2.761 0 00-1.176.386 1.115 1.115 0 00-.4.981 1.066 1.066 0 00.366.837 1.41 1.41 0 00.974.325 1.8 1.8 0 001.378-.585 2.09 2.09 0 00.543-1.479zM737.007 67.9h-1.121V57.539h1.121zM739.851 59.125a.71.71 0 01-.513-.205.69.69 0 01-.212-.52.719.719 0 01.725-.731.719.719 0 01.522.209.728.728 0 010 1.035.718.718 0 01-.522.212zm.549 8.775h-1.121v-7h1.121zM747.548 61.224l-4.143 5.722h4.1v.954h-5.749v-.349l4.144-5.691h-3.753v-.96h5.4zM754.623 64.683h-4.942a2.618 2.618 0 00.629 1.8 2.168 2.168 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.956 2.956 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.828 3.828 0 01.927-2.663 2.969 2.969 0 012.3-1.028 2.632 2.632 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.276 2.276 0 00-.469-1.511 1.6 1.6 0 00-1.281-.54 1.808 1.808 0 00-1.347.567 2.58 2.58 0 00-.684 1.483zM761.452 64.2v3.7H760.3v-9.8h2.7a3.552 3.552 0 012.437.766 2.732 2.732 0 01.865 2.16 2.971 2.971 0 01-.961 2.283 3.666 3.666 0 01-2.594.889zm0-5.059v4.02h1.2a2.688 2.688 0 001.815-.544 1.924 1.924 0 00.625-1.534q0-1.941-2.3-1.941zM770.4 68.067a3.247 3.247 0 01-2.479-.981 3.632 3.632 0 01-.926-2.6 3.784 3.784 0 01.964-2.755 3.468 3.468 0 012.6-.991 3.138 3.138 0 012.443.964 3.82 3.82 0 01.879 2.673 3.757 3.757 0 01-.947 2.683 3.314 3.314 0 01-2.534 1.007zm.082-6.385a2.13 2.13 0 00-1.709.735 3.012 3.012 0 00-.629 2.026 2.855 2.855 0 00.636 1.962 2.161 2.161 0 001.7.718 2.054 2.054 0 001.672-.7 3.059 3.059 0 00.584-2 3.113 3.113 0 00-.584-2.023 2.044 2.044 0 00-1.67-.718zM784.5 60.9l-2.1 7h-1.162l-1.442-5.011a3.223 3.223 0 01-.109-.649h-.027a3.066 3.066 0 01-.144.636l-1.569 5.024h-1.121l-2.119-7h1.176l1.449 5.264a3.241 3.241 0 01.1.629h.055a2.942 2.942 0 01.123-.643l1.613-5.25h1.025l1.449 5.277a3.8 3.8 0 01.1.629h.055a2.886 2.886 0 01.116-.629l1.422-5.277zM791.353 64.683h-4.943a2.614 2.614 0 00.629 1.8 2.167 2.167 0 001.654.636 3.441 3.441 0 002.174-.779v1.06a4.065 4.065 0 01-2.44.67 2.954 2.954 0 01-2.331-.954 3.9 3.9 0 01-.848-2.683 3.832 3.832 0 01.926-2.663 2.973 2.973 0 012.3-1.028 2.63 2.63 0 012.126.889 3.707 3.707 0 01.752 2.468zm-1.148-.95a2.286 2.286 0 00-.468-1.511 1.6 1.6 0 00-1.282-.54 1.809 1.809 0 00-1.347.567 2.574 2.574 0 00-.684 1.483zM796.7 62.037a1.372 1.372 0 00-.848-.226 1.433 1.433 0 00-1.2.677 3.136 3.136 0 00-.481 1.846V67.9h-1.121v-7h1.121v1.442h.027a2.447 2.447 0 01.731-1.152 1.67 1.67 0 011.1-.413 1.837 1.837 0 01.67.1zM801.9 67.9v-9.8h2.789a3.053 3.053 0 012.017.622 2.009 2.009 0 01.745 1.62 2.385 2.385 0 01-.451 1.449 2.432 2.432 0 01-1.244.875v.027a2.493 2.493 0 011.586.749 2.3 2.3 0 01.595 1.644 2.562 2.562 0 01-.9 2.037 3.358 3.358 0 01-2.276.779zm1.148-8.764V62.3h1.176a2.23 2.23 0 001.483-.455 1.581 1.581 0 00.54-1.281q0-1.43-1.88-1.429zm0 4.2v3.527h1.559a2.333 2.333 0 001.568-.479 1.638 1.638 0 00.558-1.312q0-1.736-2.365-1.736zM811.074 67.9h-1.148v-9.8h1.148z"/>
            </g>
            <path d="M777.6 35.017h-1.09v-2.18h1.09a4.2 4.2 0 004.195-4.195V6.375a4.2 4.2 0 00-4.195-4.2h-41.3a4.2 4.2 0 00-4.195 4.2v22.269a4.2 4.2 0 004.195 4.195h1.09v2.18h-1.09a6.382 6.382 0 01-6.374-6.375V6.375A6.382 6.382 0 01736.3 0h41.3a6.382 6.382 0 016.375 6.375v22.269a6.382 6.382 0 01-6.375 6.375"/>
            <path d="M743 27.719a2.958 2.958 0 012.958 2.958V37.5A2.958 2.958 0 01743 40.458a2.958 2.958 0 01-2.959-2.957v-6.823a2.958 2.958 0 012.958-2.958zM752.3 40.457a2.959 2.959 0 01-2.96-2.957V19.99a2.959 2.959 0 015.917 0V37.5a2.959 2.959 0 01-2.958 2.959M770.906 40.371a2.959 2.959 0 01-2.959-2.958v-24.8a2.959 2.959 0 115.917 0v24.8a2.959 2.959 0 01-2.958 2.959M761.6 40.457a2.959 2.959 0 01-2.959-2.958V24.492a2.959 2.959 0 115.917 0V37.5a2.959 2.959 0 01-2.958 2.959"/>
            <path d="M74.765 33.889H63.858c1.311 4.627-.45 5.291-8.163 5.291v2.42h26.227v-2.42c-7.713 0-8.469-.661-7.157-5.291" fill="#7a7a7a"/>
            <path d="M86.441 4.579H50.932a2.269 2.269 0 00-2.18 2.284v24.763a2.256 2.256 0 002.18 2.265h35.51a2.479 2.479 0 002.424-2.265V6.863a2.488 2.488 0 00-2.424-2.284" fill="#a0a1a2"/>
            <path d="M86.466 4.582H50.931a2.268 2.268 0 00-2.18 2.284v24.76a2.256 2.256 0 002.18 2.266h.845z" fill="#fff" opacity=".2"/>
            <path fill="#59b4d9" d="M85.734 7.667v23.137H51.792V7.667h33.942z"/>
            <path fill="#59b4d9" d="M51.792 30.804h.046V7.667l31.032-.046h.001l-31.079.046v23.137z"/>
            <path fill="#a0a1a2" d="M55.695 39.179h26.227v2.424H55.695z"/>
            <path d="M69.223 6.26a.569.569 0 11-.57-.57.57.57 0 01.57.57" fill="#b8d432"/>
            <path d="M69.246 18.534a.223.223 0 01-.108-.03l-7.063-4.077a.217.217 0 01-.106-.185.214.214 0 01.106-.185l7.025-4.051a.215.215 0 01.211 0l7.065 4.079a.215.215 0 010 .369L69.354 18.5a.216.216 0 01-.108.03" fill="#fff"/>
            <path d="M68.231 28.443a.2.2 0 01-.108-.029l-7.042-4.064a.209.209 0 01-.109-.185v-8.156a.217.217 0 01.324-.185l7.041 4.063a.224.224 0 01.1.187v8.156a.218.218 0 01-.1.185.225.225 0 01-.107.029" fill="#fff" opacity=".7"/>
            <path d="M70.225 28.443a.23.23 0 01-.111-.029.217.217 0 01-.1-.185v-8.1a.221.221 0 01.1-.185l7.041-4.063a.209.209 0 01.212 0 .211.211 0 01.108.185v8.1a.21.21 0 01-.108.185l-7.039 4.064a.19.19 0 01-.1.029" fill="#fff" opacity=".4"/>
            <g>
                <path d="M419.9 33.889h-10.911c1.311 4.627-.45 5.291-8.163 5.291v2.42h26.227v-2.42c-7.713 0-8.469-.661-7.157-5.291" fill="#7a7a7a"/>
                <path d="M431.573 4.579h-35.51a2.269 2.269 0 00-2.18 2.284v24.763a2.256 2.256 0 002.18 2.265h35.51A2.479 2.479 0 00434 31.626V6.863a2.488 2.488 0 00-2.424-2.284" fill="#a0a1a2"/>
                <path d="M431.6 4.582h-35.535a2.268 2.268 0 00-2.18 2.284v24.76a2.256 2.256 0 002.18 2.266h.845z" fill="#fff" opacity=".2"/>
                <path fill="#59b4d9" d="M430.865 7.667v23.137h-33.941V7.667h33.941z"/>
                <path fill="#59b4d9" d="M396.924 30.804h.046V7.667l31.031-.046h.002l-31.079.046v23.137z"/>
                <path fill="#a0a1a2" d="M400.827 39.179h26.227v2.424h-26.227z"/>
                <path d="M414.355 6.26a.569.569 0 11-.57-.57.57.57 0 01.57.57" fill="#b8d432"/>
                <path d="M414.377 18.534a.223.223 0 01-.108-.03l-7.063-4.077a.217.217 0 01-.106-.185.214.214 0 01.106-.185l7.021-4.051a.215.215 0 01.211 0l7.065 4.079a.215.215 0 010 .369l-7.018 4.05a.216.216 0 01-.108.03" fill="#fff"/>
                <path d="M413.363 28.443a.2.2 0 01-.108-.029l-7.042-4.064a.209.209 0 01-.109-.185v-8.156a.217.217 0 01.324-.185l7.041 4.063a.224.224 0 01.1.187v8.156a.218.218 0 01-.1.185.225.225 0 01-.107.029" fill="#fff" opacity=".7"/>
                <path d="M415.356 28.443a.23.23 0 01-.111-.029.217.217 0 01-.1-.185v-8.1a.221.221 0 01.1-.185l7.041-4.063a.209.209 0 01.212 0 .211.211 0 01.108.185v8.1a.21.21 0 01-.108.185l-7.039 4.064a.19.19 0 01-.1.029" fill="#fff" opacity=".4"/>
            </g>
            <g fill="#5b5b5b">
                <path d="M7.027 68.484H5.66l-1.64-2.748a5.973 5.973 0 00-.437-.652 2.485 2.485 0 00-.434-.441 1.539 1.539 0 00-.479-.25 2 2 0 00-.578-.078h-.944v4.17H0v-9.8h2.926a4.188 4.188 0 011.186.16 2.643 2.643 0 01.943.489 2.261 2.261 0 01.626.817 2.98 2.98 0 01.071 2.084 2.432 2.432 0 01-.437.763 2.639 2.639 0 01-.684.571 3.492 3.492 0 01-.9.365v.027a2.038 2.038 0 01.428.25 2.326 2.326 0 01.345.331 4.453 4.453 0 01.325.435c.106.161.227.35.358.563zM1.148 59.72v3.555h1.559a2.36 2.36 0 00.8-.13 1.862 1.862 0 00.632-.372 1.7 1.7 0 00.417-.6 2 2 0 00.15-.789 1.535 1.535 0 00-.51-1.227 2.18 2.18 0 00-1.473-.441zM13.357 68.484h-1.148v-9.8h1.148zM15.935 68.484v-9.8h2.707q5.181 0 5.182 4.778a4.819 4.819 0 01-1.438 3.647 5.342 5.342 0 01-3.853 1.377zm1.148-8.764v7.725h1.463a4.151 4.151 0 003-1.032 3.872 3.872 0 001.073-2.926q0-3.766-4.006-3.767zM30.946 68.484h-5.2v-9.8h4.977v1.036H26.9v3.261h3.54v1.032H26.9v3.432h4.047zM39.443 68.648a3.25 3.25 0 01-2.479-.98 3.636 3.636 0 01-.926-2.6A3.786 3.786 0 0137 62.311a3.464 3.464 0 012.6-.991 3.138 3.138 0 012.443.964 3.822 3.822 0 01.879 2.673 3.759 3.759 0 01-.947 2.684 3.317 3.317 0 01-2.532 1.007zm.082-6.385a2.133 2.133 0 00-1.709.737 3.017 3.017 0 00-.629 2.027 2.853 2.853 0 00.636 1.962 2.161 2.161 0 001.7.718A2.051 2.051 0 0041.2 67a3.063 3.063 0 00.584-2 3.115 3.115 0 00-.584-2.023 2.041 2.041 0 00-1.675-.714zM50.531 68.484H49.41v-3.993q0-2.229-1.627-2.229a1.762 1.762 0 00-1.391.633 2.34 2.34 0 00-.551 1.6v3.992h-1.12v-7h1.121v1.162h.027a2.525 2.525 0 012.3-1.326 2.14 2.14 0 011.757.742 3.3 3.3 0 01.608 2.143zM56.629 68.484v-9.8h2.707q5.181 0 5.182 4.778a4.816 4.816 0 01-1.439 3.647 5.338 5.338 0 01-3.852 1.377zm1.148-8.764v7.725h1.463a4.151 4.151 0 003-1.032 3.868 3.868 0 001.073-2.926q0-3.766-4.006-3.767zM71.921 65.264h-4.942a2.614 2.614 0 00.629 1.8 2.167 2.167 0 001.654.636 3.441 3.441 0 002.174-.779v1.053a4.058 4.058 0 01-2.44.67 2.96 2.96 0 01-2.331-.953 3.906 3.906 0 01-.848-2.684 3.826 3.826 0 01.926-2.662 2.97 2.97 0 012.3-1.029 2.633 2.633 0 012.126.889 3.706 3.706 0 01.752 2.468zm-1.148-.95A2.29 2.29 0 0070.3 62.8a1.6 1.6 0 00-1.282-.54 1.813 1.813 0 00-1.347.567 2.568 2.568 0 00-.684 1.483zM74.765 67.472h-.027V71.7h-1.122V61.484h1.121v1.23h.027a2.652 2.652 0 012.42-1.395 2.565 2.565 0 012.112.939 3.9 3.9 0 01.759 2.52 4.336 4.336 0 01-.854 2.813 2.844 2.844 0 01-2.338 1.057 2.343 2.343 0 01-2.098-1.176zm-.027-2.823v.978A2.083 2.083 0 0075.3 67.1a2.012 2.012 0 003.029-.174 3.578 3.578 0 00.577-2.167 2.827 2.827 0 00-.54-1.832 1.787 1.787 0 00-1.463-.663 1.986 1.986 0 00-1.572.68 2.5 2.5 0 00-.594 1.705zM82.968 68.484h-1.121V58.12h1.121zM88.163 68.648a3.248 3.248 0 01-2.478-.98 3.633 3.633 0 01-.927-2.6 3.786 3.786 0 01.964-2.755 3.464 3.464 0 012.6-.991 3.141 3.141 0 012.444.964 3.826 3.826 0 01.878 2.673 3.763 3.763 0 01-.944 2.681 3.321 3.321 0 01-2.537 1.008zm.082-6.385a2.134 2.134 0 00-1.709.737 3.022 3.022 0 00-.629 2.027 2.853 2.853 0 00.636 1.962 2.161 2.161 0 001.7.718 2.046 2.046 0 001.671-.7 3.052 3.052 0 00.585-2 3.1 3.1 0 00-.585-2.023 2.036 2.036 0 00-1.669-.721zM99.012 61.484l-3.22 8.116q-.861 2.174-2.42 2.174a2.549 2.549 0 01-.731-.089v-1a2.078 2.078 0 00.663.123 1.374 1.374 0 001.271-1.008l.561-1.326-2.736-6.99h1.244l1.894 5.387q.034.1.144.533h.041c.022-.109.068-.283.137-.52l1.989-5.4zM105.772 65.264h-4.942a2.614 2.614 0 00.629 1.8 2.167 2.167 0 001.654.636 3.441 3.441 0 002.174-.779v1.053a4.058 4.058 0 01-2.44.67 2.96 2.96 0 01-2.331-.953 3.906 3.906 0 01-.848-2.684 3.826 3.826 0 01.926-2.662 2.97 2.97 0 012.3-1.029 2.633 2.633 0 012.126.889 3.706 3.706 0 01.752 2.468zm-1.148-.95a2.29 2.29 0 00-.468-1.511 1.6 1.6 0 00-1.282-.54 1.813 1.813 0 00-1.347.567 2.568 2.568 0 00-.684 1.483zM113.442 68.484h-1.121v-1.19h-.027a2.824 2.824 0 01-4.515.414 3.853 3.853 0 01-.79-2.561 4.2 4.2 0 01.875-2.782 2.885 2.885 0 012.336-1.045 2.246 2.246 0 012.1 1.135h.027V58.12h1.121zm-1.121-3.165v-1.033a2 2 0 00-.561-1.436 1.878 1.878 0 00-1.422-.588 1.934 1.934 0 00-1.613.752 3.3 3.3 0 00-.588 2.078A2.967 2.967 0 00108.7 67a1.844 1.844 0 001.515.7 1.913 1.913 0 001.521-.677 2.516 2.516 0 00.585-1.704zM126.984 58.681l-3.63 9.8h-1.264l-3.555-9.8h1.278l2.714 7.772a4.7 4.7 0 01.2.868h.027a4.217 4.217 0 01.226-.882l2.769-7.759zM138.387 68.484h-1.142v-6.577q0-.779.1-1.907h-.027a6.158 6.158 0 01-.294.95l-3.35 7.533h-.561l-3.343-7.479a5.8 5.8 0 01-.294-1h-.027q.054.587.055 1.921v6.563h-1.107v-9.8h1.518l3.008 6.836a8.719 8.719 0 01.451 1.176h.041c.2-.537.354-.939.472-1.2l3.069-6.809h1.436z"/>
            </g>
        </g>
    </g>
</svg>

## Description

Required preliminary agreement: You need to accept the Terms of Use for the Data Science Virtual Machine on your Azure Subscription before you deploy this VM the first time. Click here to agree to these terms.

## Overview

This solution enables a predictive model for Length of Stay for in-hospital admissions. Length of Stay (LOS) is defined in number of days from the initial admit date to the date that the patient is discharged from any given hospital facility. There can be significant variation of LOS across various facilities and across disease conditions and specialties even within the same healthcare system. Advanced LOS prediction at the time of admission can greatly enhance the quality of care as well as operational workload efficiency and help with accurate planning for discharges resulting in lowering of various other quality measures such as readmissions.

## Business Perspective

There are two different business users in hospital management who can expect to benefit from more reliable predictions of the Length of Stay. These are:

  * The Chiefs Medical Information Officer (CMIO), who straddles the divide between informatics/technology and healthcare professionals in a healthcare organization. Their duties typically include using analytics to determine if resources are being allocated appropriately in a hospital network. As part of this, the CMIO needs to be able to determine which facilities are being overtaxed and, specifically, what resources at those facilities may need to be bolstered to realign such resources with demand.
  * The Care Line Manager, who is directly involved with the care of patients. This role requires monitoring the status of individual patients as well as ensuring that staff is available to meet the specific care requirements of their patients. A Care Line Manager also needs to manage the discharge of their patients. The ability to predict LOS of a patient enables Care Line Managers to determine if staff resources will be adequate to handle the release of a patient.

## Data Scientist Perspective

SQL Server R Services brings the computing resources to the data by running R on the computer that hosts the database. It includes a database service that runs outside the SQL Server process and that communicates securely with the R runtime.

This solution walks through the steps needed to create and refine data, train the R models, and perform scoring on the SQL Server machine. The final scored database table in SQL Server gives the predicted LOS for each patient. This data is then visualized in PowerBI. (Simulated data is used in this template to illustrate the feature.)

Data scientists who are testing and developing solutions can work conveniently from their preferred R IDE on their client machine, while pushing the compute to the SQL Server machine. The completed solutions are deployed to SQL Server 2016 by embedding calls to R in stored procedures. These solutions can then be further automated with SQL Server Integration Services and SQL Server agent.

This solution includes the R code needed by a data scientist in the R folder. It shows the stored procedures (.sql files) that can be deployed in the SQLR folder. A PowerShell script (.ps1 file) is also provided that automates the running of the SQL code. Click on the Deploy button to test the automation and the entire solution will be made available in your Azure subscription.

## Pricing

Your Azure subscription used for the deployment will incur consumption charges on the services used in this solution, approximately $1.15/hour for the default VM.

Please ensure that you stop your VM instance when not actively using the solution. Running the VM will incur higher costs.

Please delete the solution if you are not using it.

[!INCLUDE [js_include_file](../../_js/index.md)]