
                    
                    <div class="visual-example">
                        
                        <div class="examples-container">
                            <div class="example-nav">
                                <button onclick="previousReasoningExample()" class="nav-button">←</button>
                                <span id="reasoning-counter">Example 1/2</span>
                                <button onclick="nextReasoningExample()" class="nav-button">→</button>
                            </div>
                        
                            <div class="examples">
                                <!-- Original Butterfly Example -->
                                <div class="example active" data-index="0">
                                    <div class="prompt-box">
                                        "Generate an image of the animal resulting from a monarch caterpillar's metamorphosis"
                                    </div>
                        
                                    <div class="result-image">
                                        <img src="static/img/butterfly.png" alt="Monarch Butterfly">
                                    </div>
                                    
                                    <div class="reasoning-process" onclick="event.stopPropagation()">
                                        <div class="process-header">Model's Implicit Reasoning Process</div>
                                        <div class="steps-progress">
                                            <div class="step-dot active" onclick="showStep(0, 0)">1</div>
                                            <div class="step-line"></div>
                                            <div class="step-dot" onclick="showStep(0, 1)">2</div>
                                            <div class="step-line"></div>
                                            <div class="step-dot" onclick="showStep(0, 2)">3</div>
                                        </div>
                                        
                                        <div class="steps-content">
                                            <div class="step-box" data-step="0">
                                                <div class="step-title">Initial Understanding</div>
                                                <div class="step-detail">Identifies the starting point: monarch caterpillar</div>
                                            </div>
                                            <div class="step-box hidden" data-step="1">
                                                <div class="step-title">Process Knowledge</div>
                                                <div class="step-detail">Applies understanding of metamorphosis lifecycle</div>
                                            </div>
                                            <div class="step-box hidden" data-step="2">
                                                <div class="step-title">Final Transformation</div>
                                                <div class="step-detail">Determines the end result: monarch butterfly</div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                        
                                <!-- New American Flag Example -->
                                <div class="example" data-index="1">
                                    <div class="prompt-box">
                                        "Generate an image of the national flag of the country where Yellowstone National Park is located"
                                    </div>
                        
                                    <div class="result-image">
                                        <img src="static/img/usa_flag.png" alt="American Flag">
                                    </div>
                                    
                                    <div class="reasoning-process" onclick="event.stopPropagation()">
                                        <div class="process-header">Model's Implicit Reasoning Process</div>
                                        <div class="steps-progress">
                                            <div class="step-dot active" onclick="showStep(1, 0)">1</div>
                                            <div class="step-line"></div>
                                            <div class="step-dot" onclick="showStep(1, 1)">2</div>
                                            <div class="step-line"></div>
                                            <div class="step-dot" onclick="showStep(1, 2)">3</div>
                                        </div>
                                        
                                        <div class="steps-content">
                                            <div class="step-box" data-step="0">
                                                <div class="step-title">Geographic Knowledge</div>
                                                <div class="step-detail">Locates Yellowstone National Park</div>
                                            </div>
                                            <div class="step-box hidden" data-step="1">
                                                <div class="step-title">Country Identification</div>
                                                <div class="step-detail">Recognizes Yellowstone is in United States</div>
                                            </div>
                                            <div class="step-box hidden" data-step="2">
                                                <div class="step-title">Symbol Generation</div>
                                                <div class="step-detail">Generates the American flag based on national symbol knowledge</div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <script>
                            let currentReasoningExample = 0;
                            const totalReasoningExamples = 2;
                            
                            function showReasoningExample(index) {
                                document.querySelectorAll('.example').forEach(ex => {
                                    ex.style.display = 'none';
                                    ex.classList.remove('active');
                                });
                                document.querySelector(`.example[data-index="${index}"]`).style.display = 'block';
                                document.querySelector(`.example[data-index="${index}"]`).classList.add('active');
                                document.getElementById('reasoning-counter').textContent = `Example ${index + 1}/${totalReasoningExamples}`;
                            }
                            
                            function nextReasoningExample() {
                                currentReasoningExample = (currentReasoningExample + 1) % totalReasoningExamples;
                                showReasoningExample(currentReasoningExample);
                            }
                            
                            function previousReasoningExample() {
                                currentReasoningExample = (currentReasoningExample - 1 + totalReasoningExamples) % totalReasoningExamples;
                                showReasoningExample(currentReasoningExample);
                            }
                            
                            function showStep(exampleIndex, stepIndex) {
                                // Hide all steps for this example
                                const steps = document.querySelectorAll(`.example[data-index="${exampleIndex}"] .step-box`);
                                steps.forEach(step => step.classList.add('hidden'));
                                
                                // Show current step
                                const currentStep = document.querySelector(`.example[data-index="${exampleIndex}"] .step-box[data-step="${stepIndex}"]`);
                                currentStep.classList.remove('hidden');
                                
                                // Update dots
                                const dots = document.querySelectorAll(`.example[data-index="${exampleIndex}"] .step-dot`);
                                dots.forEach((dot, index) => {
                                    if (index <= stepIndex) {
                                        dot.classList.add('active');
                                    } else {
                                        dot.classList.remove('active');
                                    }
                                });
                        }
                        </script>
                            

                    <style>
                        .examples-container {
                            padding: 1rem;
                        }
                        
                        .prompt-box {
                            background: linear-gradient(135deg, var(--primary), var(--accent));
                            padding: 1rem 1.5rem;
                            border-radius: 0.75rem;
                            color: white;
                            font-size: 1.1rem;
                            line-height: 1.5;
                            margin-bottom: 1.5rem;
                            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
                        }
                        
                        .examples {
                            display: flex;
                            flex-direction: column;
                            align-items: center;
                        }

                        .example {
                            width: 100%;         /* Ensure example takes full width */
                            display: flex;
                            flex-direction: column;
                            align-items: center;  /* Center all content within example */
                            position: relative;   /* Add this */

                        }

                        .prompt-box {
                            width: 100%;         /* Full width for prompt box */
                        }

                        .result-image {
                            margin: 1.5rem auto;  /* Change 1.5rem 0 to 1.5rem auto */
                            padding: 0.5rem;
                            width: 50%;
                            display: flex;
                            justify-content: center;
                            align-items: center;
                            background: white;
                            border-radius: 0.75rem;
                            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
                        }

                        .result-image img {
                            border-radius: 0.5rem;
                        }

                                                                        


                        .reasoning-process {
                            background: #f8fafc;
                            padding: 1.5rem;
                            border-radius: 1rem;
                            margin-top: 1.5rem;
                        }
                        
                        .process-header {
                            text-align: center;
                            color: var(--primary);
                            font-weight: 600;
                            margin-bottom: 1.5rem;
                            font-size: 1.1rem;
                        }
                        
                        .steps-progress {
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            margin-bottom: 1.5rem;
                        }
                        
                        .step-dot {
                            width: 32px;
                            height: 32px;
                            border-radius: 50%;
                            background: white;
                            border: 2px solid #e5e7eb;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            font-weight: 600;
                            color: #6b7280;
                            cursor: pointer;
                            transition: all 0.3s ease;
                        }
                        
                        .step-dot:hover {
                            transform: translateY(-2px);
                            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
                        }
                        
                        .step-dot.active {
                            background: var(--primary);
                            border-color: var(--primary);
                            color: white;
                        }
                        
                        .step-line {
                            height: 2px;
                            width: 80px;
                            background: #e5e7eb;
                            margin: 0 8px;
                        }
                        
                        .steps-content {
                            position: relative;
                            min-height: 100px;
                        }
                        
                        .step-box {
                            background: white;
                            padding: 1.5rem;
                            border-radius: 0.75rem;
                            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
                            position: absolute;
                            width: 100%;
                            transition: all 0.3s ease;
                            opacity: 1;
                            transform: translateY(0);
                        }
                        
                        .step-box.hidden {
                            opacity: 0;
                            transform: translateY(10px);
                            pointer-events: none;
                        }
                        
                        .step-title {
                            color: var(--primary);
                            font-weight: 600;
                            margin-bottom: 0.5rem;
                        }
                        
                        .step-detail {
                            color: #4b5563;
                            line-height: 1.5;
                        }
                        
                        .reveal-prompt {
                            text-align: center;
                            color: #6b7280;
                            font-size: 0.9rem;
                            margin-top: 1.5rem;
                        }
                        
                        .example-nav {
                            display: flex;
                            justify-content: space-between;
                            align-items: center;
                            margin-bottom: 1.5rem;
                        }
                        
                        .nav-button {
                            background: white;
                            border: 1px solid rgba(0, 0, 0, 0.1);
                            cursor: pointer;
                            font-size: 1.25rem;
                            color: var(--primary);
                            padding: 0.75rem 1rem;
                            border-radius: 0.75rem;
                            transition: all 0.2s ease;
                        }
                        
                        .nav-button:hover {
                            background: var(--primary);
                            color: white;
                            transform: translateY(-1px);
                            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
                        }
                        
                        #reasoning-counter {
                            font-size: 0.95rem;
                            color: #4b5563;
                            font-weight: 500;
                            background: #f8fafc;
                            padding: 0.5rem 1rem;
                            border-radius: 0.5rem;
                            border: 1px solid rgba(0, 0, 0, 0.05);
                        }
                        
                        @keyframes fadeInUp {
                            from {
                                opacity: 0;
                                transform: translateY(10px);
                            }
                            to {
                                opacity: 1;
                                transform: translateY(0);
                            }
                        }
                        
                        .step-box:not(.hidden) {
                            animation: fadeInUp 0.3s ease forwards;
                        }
                    </style>